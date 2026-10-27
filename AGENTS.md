# AGENTS.md — Laboratorio Coffee Medallion + IA de Snowflake

Estas reglas aplican a **toda** conversación con Cortex Code en este workspace.
Son obligatorias. Si el participante pide algo que las contradiga, explica la regla y propone la alternativa compatible.

## 1. Contexto
- Laboratorio para llevar una fuente de datos desde **Bronze → Silver → Gold** y construir un producto final
  (semantic view, Cortex Agent, dashboard Streamlit) con la IA de Snowflake: **Cortex Code** genera el pipeline y **Cortex Analyst / Agents** consumen el resultado.
- Para ejecutar el flujo completo usa el skill **`medallion-builder`** (`.cortex/skills/medallion-builder/SKILL.md`).
- Estándares detallados en `standards/`. Léelos antes de crear objetos:
  - `standards/naming.md` (nombres — **siempre**)
  - `standards/bronze.md`, `standards/silver.md`, `standards/gold.md`
  - `standards/ai_functions.md` (política: sin enriquecimiento AISQL)
- Plantillas SQL de referencia en `templates/`.

## 2. Infraestructura fija (NO crear otras bases de datos)
| Capa   | Base de datos   | Propósito |
|--------|-----------------|-----------|
| Bronze | `COFFEE_BRONZE` | Copia fiel de los archivos (sin transformar) |
| Silver | `COFFEE_SILVER` | Limpieza, tipado, deduplicación, modelo dimensional |
| Gold   | `COFFEE_GOLD`   | Métricas, semantic views, agentes, dashboards |

- Datasets fuente: `@COFFEE_BRONZE.LANDING.STG_DATASETS/<fuente>/` (solo lectura).
  Hay 45 fuentes por rubro, cada una en su carpeta con un único CSV consolidado. Prefijos: \anca_\, \seguros_\, etail_\, \limentos_\, \vicola_\, \gro_\,
  \cemento_\, \pinturas_\, \energia_\, \	elecom_\, \gua_\, \gobierno_\, \petroleo_\, \	extil_\, \utomotriz_\, \educacion_\, \	i_\, \software_\, \servicios_ti_\.
  Columnas, grano y cuidados de cada una: **\datasets/CATALOGO.md\** — léelo antes de procesar una fuente.
  Si el participante dice solo el tema (p. ej. «ventas»), propón las fuentes que coinciden y pregunta cuál.
- File formats: `COFFEE_BRONZE.LANDING.FF_CSV`, `FF_JSON`, `FF_PARQUET`.
- Rol: `COFFEE_LAB_PARTICIPANT`. Warehouse: `COMPUTE_WH`.

## 3. Identidad del participante (obligatorio antes de crear nada)
1. Obtén nombre y apellido del participante (pregúntalo si no lo dio).
2. Calcula `INI` = primera letra del primer nombre + primera letra del primer apellido, en MAYÚSCULAS
   (Gustavo Gamboa → `GG`).
3. Si ya existe un esquema `<INI>_<FUENTE>` cuyo `COMMENT` corresponde a otra persona, usa
   primera letra del nombre + dos primeras del apellido (`GGA`).
4. Esquema de trabajo en cada capa: `<INI>_<FUENTE>` (ej. `COFFEE_SILVER.GG_VENTAS`).

## 4. Reglas de oro
- Usa siempre el rol `USE ROLE COFFEE_LAB_PARTICIPANT;` — **nunca** ACCOUNTADMIN.
- Nombres completamente calificados `BASE.ESQUEMA.OBJETO` en todo SQL.
- **Nunca** modifiques, elimines ni leas de esquemas de otros participantes ni de `COFFEE_BRONZE.LANDING` (solo leer el stage).
- Todo objeto lleva `COMMENT` con: `'<descripción> | owner: <Nombre Apellido> | fuente: <FUENTE>'`.
- Idempotencia: `CREATE OR REPLACE` / `IF NOT EXISTS`. Los scripts deben poder re-ejecutarse.
- **Validar que el nombre no exista antes de crear** (esquema, tabla, vista, dynamic table, semantic view, agente, procedimiento, app):
  consulta con `SHOW <TIPO> LIKE '<NOMBRE>' IN SCHEMA ...` o `INFORMATION_SCHEMA` **antes** de cada `CREATE`.
  - No existe → créalo.
  - Existe y su `COMMENT` dice `owner:` el mismo participante → díselo en el plan y reemplázalo solo con su confirmación.
  - Existe y es de otra persona → no lo toques; aplica la regla de colisión de INI (sección 3) o propón otro nombre.
- **Procedimiento único de reproceso**: todo esquema de trabajo termina con **un solo** procedimiento
  `COFFEE_GOLD.<INI>_<FUENTE>.SP_REFRESH_<FUENTE>()` que, con un `CALL` y sin pasos manuales, reprocesa todo desde cero:
  recarga Bronze (vaciar `RAW_` + `COPY INTO` sin duplicar), refresca Silver y Gold en orden de dependencias y devuelve el conteo de filas por objeto.
  Debe poder ejecutarse las veces que se quiera con el mismo resultado. Plantilla: `templates/05_refresh.sql`. Ver `standards/gold.md`.
- **Frecuencia de actualización**: por defecto `TARGET_LAG = '1 day'` en las dynamic tables. Si el participante pide refrescar con más frecuencia
  (`'1 hour'`, `'5 minutes'`, `DOWNSTREAM`, etc.) o pide una task (`TSK_`), hazlo sin objeciones; solo deja la frecuencia elegida en el `COMMENT` y en el resumen final.
- **No** usar funciones AISQL de enriquecimiento (AI_SENTIMENT, AI_EXTRACT, AI_CLASSIFY, AI_COMPLETE, AI_SUMMARIZE_AGG…):
  consumen muchos tokens y están fuera del alcance. La IA del laboratorio es Cortex Code + semantic view + Cortex Agent.
  Ver `standards/ai_functions.md`.
- Al terminar cada capa ejecuta las validaciones del estándar y reporta conteos.
- Guarda el SQL generado en el workspace: `participants/<INI>_<FUENTE>/01_bronze.sql`, `02_silver.sql`, `03_gold.sql`, `04_product.sql`, `05_refresh.sql`.

## 5. Prompt esperado del participante
> "Soy **Gustavo Gamboa**. Procesa la fuente **VENTAS** de bronze a gold y quiero un **agente** y un **dashboard** de ventas por tienda y producto."

Con eso basta: usa el skill `medallion-builder` y sigue los estándares (incluida la validación de nombres, el `SP_REFRESH_<FUENTE>` y el `TARGET_LAG` por defecto de 1 día).

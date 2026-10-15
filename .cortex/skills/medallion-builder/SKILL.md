---
name: medallion-builder
description: Lleva una fuente de datos del stage COFFEE_BRONZE.LANDING.STG_DATASETS de Bronze a Silver a Gold siguiendo los estándares del laboratorio Coffee, y construye el producto final (semantic view, Cortex Agent, dashboard Streamlit) a partir de fuentes estructuradas, sin funciones AISQL de enriquecimiento. Triggers: procesa la fuente, de bronze a gold, medallion, pipeline del laboratorio, crea agente/dashboard de mi fuente.
---

# Medallion Builder — Laboratorio Coffee

## Antes de empezar (obligatorio)
1. Lee `AGENTS.md` y `standards/naming.md`, `standards/bronze.md`, `standards/silver.md`, `standards/gold.md`, `standards/ai_functions.md`.
2. Extrae del prompt del participante:
   - **Nombre y apellido** → calcula `INI`.
   - **FUENTE** (carpeta del stage).
   - **Producto final**: agente, dashboard, reporte (puede ser más de uno). Si no lo indicó, por defecto: semantic view + agente.
   - **Qué quiere ver** (métricas/preguntas de negocio).
   Si falta nombre o fuente, pregúntalo con una sola pregunta. Si la fuente no existe, muestra las disponibles:
   `LIST @COFFEE_BRONZE.LANDING.STG_DATASETS;`
3. `USE ROLE COFFEE_LAB_PARTICIPANT; USE WAREHOUSE COMPUTE_WH;`
4. Revisa colisión de esquema: `SHOW SCHEMAS LIKE '<INI>_<FUENTE>' IN DATABASE COFFEE_BRONZE;` (ver regla en AGENTS.md).
5. Presenta un plan corto (objetos a crear por capa con sus FQN) y pide confirmación una vez.

## Paso 1 — Bronze
- Seguir `standards/bronze.md` y `templates/01_bronze.sql`.
- Perfilar archivos (`INFER_SCHEMA`), crear `RAW_<ENTIDAD>` y cargar con `COPY INTO`.
- Guardar SQL en `participants/<INI>_<FUENTE>/01_bronze.sql`. Reportar conteos.

## Paso 2 — Silver
- Perfilar RAW_: nulos, duplicados, tipos.
- Crear `STG_` → `DIM_` / `FCT_` según `standards/silver.md`, `templates/02_silver.sql`.
- **No** usar funciones AISQL (AI_SENTIMENT, AI_EXTRACT, etc.) ni tablas `ENR_`.
- Guardar en `02_silver.sql`. Ejecutar validaciones.

## Paso 3 — Gold
- Crear `AGG_` y `KPI_` alineados a lo que el participante quiere ver.
- Crear `SV_<FUENTE>` (skill `agent-studio`). Validar con 3 preguntas.
- Guardar en `03_gold.sql`.

## Paso 4 — Producto final
- Agente → `AGT_<FUENTE>` (skill `agent-studio`), tool Cortex Analyst sobre `SV_<FUENTE>` .
- Dashboard → `APP_<FUENTE>_DASHBOARD` en Streamlit (skill `streamlit-in-workspaces`), en `participants/<INI>_<FUENTE>/app/`, leyendo solo de Gold.
- Guardar en `04_product.sql`.

## Cierre
Entrega al participante:
- Tabla resumen de objetos creados por capa (FQN) y conteos.
- 3 preguntas de ejemplo para el agente / cómo abrir el dashboard.

## Prohibido
- Crear bases de datos, usar ACCOUNTADMIN, tocar esquemas de otros participantes, escribir en `COFFEE_BRONZE.LANDING`.
- Funciones AISQL de enriquecimiento (AI_SENTIMENT, AI_EXTRACT, AI_CLASSIFY, AI_COMPLETE, AI_SUMMARIZE_AGG…).
- Objetos sin COMMENT o con nombres fuera de estándar.

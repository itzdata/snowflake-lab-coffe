# Estándar Silver — `COFFEE_SILVER.<INI>_<FUENTE>`

**Objetivo:** datos confiables y modelados (modelo dimensional).

## 1. STG_ (1:1 con cada RAW_)
- Tipar columnas (`TRY_TO_NUMBER`, `TRY_TO_DATE`, `TRY_TO_TIMESTAMP`) — nunca casts que fallen.
- Renombrar columnas al estándar (`standards/naming.md`).
- `TRIM`, `INITCAP`/`UPPER` en catálogos, normalizar nulos (`NULLIF(TRIM(x), '')`).
- Deduplicar con `QUALIFY ROW_NUMBER() OVER (PARTITION BY <llave> ORDER BY _LOADED_TS DESC) = 1`.
- Agregar `_UPDATED_TS = CURRENT_TIMESTAMP()`.
- Materialización recomendada: **dynamic table** `TARGET_LAG = '24 hours'`, `WAREHOUSE = COMPUTE_WH`
  (o tabla CTAS si el participante prefiere simplicidad). Si es DT, nombre `STG_<ENTIDAD>` igual (el prefijo `DT_` es opcional).

## 2. Sin enriquecimiento con IA
No usar funciones AISQL (`AI_SENTIMENT`, `AI_EXTRACT`, etc.) ni crear tablas `ENR_`. Ver `standards/ai_functions.md`.
Las columnas de texto se limpian (`TRIM`) y se conservan tal cual; las reglas de negocio se hacen con SQL (`CASE`).

## 3. Modelo dimensional
- `DIM_<ENTIDAD>`: llave sustituta `<ENTIDAD>_SK` (`HASH(<llave natural>)` o secuencia), atributos descriptivos.
- `DIM_DATE`: generar con `GENERATOR` entre min y max de fechas de la fuente.
- `FCT_<PROCESO>`: granularidad documentada en el COMMENT, llaves `_SK` hacia dimensiones, medidas `_AMT`, `_QTY`.

## Validación
- Unicidad de llaves: `COUNT(*) = COUNT(DISTINCT <llave>)` en STG y DIM.
- Integridad referencial: hechos sin dimensión = 0.
- % nulos en columnas clave < umbral acordado; reportarlo.

Plantilla: `templates/02_silver.sql`.

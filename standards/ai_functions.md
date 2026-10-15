# Política de IA del laboratorio

Este laboratorio muestra la IA de Snowflake a través de **Cortex Code** (genera el pipeline), **Cortex Analyst**
(semantic views) y **Cortex Agents**. **No** incluye enriquecimiento de datos con funciones AISQL fila por fila,
porque consume muchos tokens (ese tema queda para un curso dedicado).

## Prohibido en el pipeline
- `AI_SENTIMENT`, `AI_CLASSIFY`, `AI_EXTRACT`, `AI_TRANSLATE`, `AI_FILTER`, `AI_COMPLETE`, `AI_AGG`,
  `AI_SUMMARIZE_AGG`, `AI_PARSE_DOCUMENT`, `AI_EMBED`, `AI_SIMILARITY` y las funciones `SNOWFLAKE.CORTEX.*` equivalentes.
- Tablas `ENR_` (enriquecidas con IA).

Si el participante lo pide, explícale que está fuera del alcance del laboratorio y continúa con SQL tradicional
(por ejemplo, clasificar con `CASE`/reglas, o contar palabras clave con `ILIKE`).

## Permitido
- Semantic view `SV_` + Cortex Analyst.
- Cortex Agent `AGT_` (consume tokens solo cuando el usuario le hace preguntas).

Todas las fuentes del stage son **estructuradas** (CSV/JSON/Parquet tabulares): no se usa Cortex Search ni
procesamiento de documentos.

# Estándar Gold — `COFFEE_GOLD.<INI>_<FUENTE>`

**Objetivo:** productos de datos listos para consumo de negocio e IA.

## 1. Métricas (siempre)
- `AGG_<PROCESO>_<GRANO>` (ej. `AGG_SALES_DAILY_STORE`): tablas o dynamic tables agregadas desde `FCT_` + `DIM_`.
- `KPI_<PROCESO>`: vista con KPIs de negocio (totales, ticket promedio, variación vs periodo anterior).
- Sin funciones AISQL (ver `standards/ai_functions.md`).

## 2. Semantic view (siempre) — `SV_<FUENTE>`
- Basada en `FCT_` y `DIM_` de Silver (o AGG_ de Gold).
- Definir TABLES (con PRIMARY KEY), RELATIONSHIPS, FACTS, DIMENSIONS, METRICS; con `SYNONYMS` y `COMMENT` en español.
- Validar con `SELECT * FROM SEMANTIC_VIEW(...)` y con `cortex analyst query`.
- Para crearla o mejorarla usar el skill integrado **`agent-studio`**.

## 3. Producto final (según el prompt)
| Pide | Crear | Notas |
|---|---|---|
| Agente / chat / preguntas en lenguaje natural | `AGT_<FUENTE>` | Cortex Agent con tool Cortex Analyst → `SV_<FUENTE>`. Skill `agent-studio`. |
| Dashboard / visualización | `APP_<FUENTE>_DASHBOARD` | Streamlit leyendo solo de Gold (AGG_/KPI_). Skill `streamlit-in-workspaces`. |
| Reporte | Notebook o HTML en `participants/<INI>_<FUENTE>/` | |

## Validación final
- Cada AGG_ cuadra con FCT_ (suma total igual).
- La semantic view responde 3 preguntas de prueba.
- El agente responde 1 pregunta de prueba (`DATA_AGENT_RUN` o desde Snowsight).
- Mostrar al participante un resumen: objetos creados por capa (FQN) y cómo usarlos.

Plantilla: `templates/03_gold.sql`.

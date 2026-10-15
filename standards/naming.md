# Estándar de nombres

Formato general: `UPPER_SNAKE_CASE`, sin acentos, sin espacios, sin comillas dobles. Inglés o español, pero consistente dentro de una fuente.

## Bases y esquemas
| Elemento | Patrón | Ejemplo |
|---|---|---|
| Base de datos | `COFFEE_<CAPA>` (fijas) | `COFFEE_SILVER` |
| Esquema de trabajo | `<INI>_<FUENTE>` | `GG_VENTAS` |
| INI | 1ª letra nombre + 1ª letra apellido (colisión: + 2ª letra apellido) | `GG`, `GGA` |
| FUENTE | nombre de la carpeta del stage, en mayúsculas | `@STG_DATASETS/ventas/` → `VENTAS` |

## Prefijos de objetos por capa
| Capa | Prefijo | Tipo de objeto | Ejemplo |
|---|---|---|---|
| Bronze | `RAW_` | Tabla cruda cargada con COPY INTO | `COFFEE_BRONZE.GG_VENTAS.RAW_ORDERS` |
| Silver | `STG_` | Limpieza/tipado 1:1 con RAW | `COFFEE_SILVER.GG_VENTAS.STG_ORDERS` |
| Silver | `DIM_` | Dimensión | `DIM_PRODUCT` |
| Silver | `FCT_` | Hecho | `FCT_SALES` |
| Gold | `AGG_` | Agregado | `AGG_SALES_DAILY_STORE` |
| Gold | `KPI_` | Vista de KPIs | `KPI_SALES` |
| Gold | `SV_` | Semantic view | `SV_VENTAS` |
| Gold | `AGT_` | Cortex Agent | `AGT_VENTAS` |
| Gold | `APP_` | Streamlit app / dashboard | `APP_VENTAS_DASHBOARD` |

## Objetos de pipeline (cualquier capa)
| Prefijo | Objeto |
|---|---|
| `DT_` | Dynamic table (si se usa en vez de tabla; ej. `DT_STG_ORDERS`) |
| `VW_` | Vista auxiliar |
| `STRM_` | Stream |
| `TSK_` | Task |
| `PIPE_` | Snowpipe |
| `FN_` / `SP_` | Función / procedimiento |

## Columnas
| Tipo | Patrón | Ejemplo |
|---|---|---|
| Llave natural | `<ENTIDAD>_ID` | `ORDER_ID` |
| Llave sustituta | `<ENTIDAD>_SK` | `PRODUCT_SK` |
| Fecha | `<X>_DATE` | `ORDER_DATE` |
| Timestamp | `<X>_TS` | `CREATED_TS` |
| Booleano | `IS_<X>` / `HAS_<X>` | `IS_ACTIVE` |
| Monto | `<X>_AMT` | `TOTAL_AMT` |
| Cantidad | `<X>_QTY` | `ITEM_QTY` |
| Conteo | `<X>_CNT` | `ORDER_CNT` |
| Porcentaje | `<X>_PCT` | `MARGIN_PCT` |
| Auditoría | `_FILE_NAME`, `_FILE_ROW`, `_LOADED_TS` (Bronze), `_UPDATED_TS` (Silver) | |

## COMMENT obligatorio
`'<descripción> | owner: <Nombre Apellido> | fuente: <FUENTE>'`

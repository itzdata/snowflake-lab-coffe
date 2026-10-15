# Estándar Bronze — `COFFEE_BRONZE.<INI>_<FUENTE>`

**Objetivo:** copia fiel de los archivos. Sin limpiar, sin renombrar valores, sin filtrar.

## Pasos
1. Descubrir archivos:
   ```sql
   LIST @COFFEE_BRONZE.LANDING.STG_DATASETS/<fuente>/;
   ```
2. Crear el esquema:
   ```sql
   CREATE SCHEMA IF NOT EXISTS COFFEE_BRONZE.<INI>_<FUENTE> COMMENT = '... | owner: ... | fuente: ...';
   ```
3. Por cada archivo/entidad (un archivo o patrón = una tabla `RAW_<ENTIDAD>`):
   - CSV/Parquet: `CREATE TABLE ... USING TEMPLATE (SELECT ARRAY_AGG(OBJECT_CONSTRUCT(*)) FROM TABLE(INFER_SCHEMA(...)))`
     y luego `COPY INTO ... MATCH_BY_COLUMN_NAME = CASE_INSENSITIVE`.
   - JSON: tabla con columna `RAW VARIANT` + columnas de auditoría.
4. Agregar columnas de auditoría: `_FILE_NAME` (METADATA$FILENAME), `_FILE_ROW` (METADATA$FILE_ROW_NUMBER), `_LOADED_TS`.
   Use `INCLUDE_METADATA` en COPY o un COPY con transformación `SELECT`.
5. `ON_ERROR = CONTINUE` y reportar errores con `VALIDATE()` si hubo filas rechazadas.

## Validación
- `SELECT COUNT(*)` por tabla RAW vs filas reportadas por COPY.
- Nombres de columnas normalizados a MAYÚSCULAS (INFER_SCHEMA lo hace con `IGNORE_CASE => TRUE`).

Plantilla: `templates/01_bronze.sql`.

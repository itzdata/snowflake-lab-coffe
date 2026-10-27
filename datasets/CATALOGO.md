# Datasets del laboratorio

20 fuentes sintéticas, 3 industrias (banca, retail, alimentos). Cada fuente es **una carpeta con un único archivo CSV consolidado**
(UTF-8, con encabezado, fechas ISO). El nombre de la carpeta es el nombre de la FUENTE que se usa en el prompt y en el esquema `<INI>_<FUENTE>`.

Stage destino: `@COFFEE_BRONZE.LANDING.STG_DATASETS/<fuente>/<fuente>.csv`  ·  File format: `COFFEE_BRONZE.LANDING.FF_CSV`

Los datos son ficticios. Cubren enero 2025 a junio 2026 (salvo donde se indica), en USD, con operación en Panamá, Costa Rica, Guatemala, Colombia,
República Dominicana, El Salvador y Honduras.

## Catálogo

| # | Industria | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|---|
| 01 | Banca | `banca_transacciones_tarjeta` | Compras con tarjeta de débito y crédito en comercios, e-commerce, ATM y contactless. | 30,120 | 16 |
| 02 | Banca | `banca_prestamos` | Cartera de préstamos desembolsados (personal, hipotecario, vehicular, pyme, libre inversión). | 6,012 | 16 |
| 03 | Banca | `banca_cartera_morosidad` | Foto de la cartera vigente al 30-jun-2026 con días de mora, provisión y gestión de cobranza. | 4,698 | 13 |
| 04 | Banca | `banca_cuentas_movimientos` | Movimientos de cuentas de ahorro, corriente y nómina (depósitos, retiros, transferencias, pagos). | 30,120 | 11 |
| 05 | Banca | `banca_atencion_clientes` | Casos de servicio al cliente (reclamos, consultas, solicitudes) con SLA y satisfacción. | 8,024 | 14 |
| 06 | Banca | `banca_alertas_fraude` | Alertas del motor antifraude sobre transacciones con tarjeta y su resultado de revisión. | 5,010 | 13 |
| 07 | Banca | `banca_operaciones_agencias` | Operación diaria de 20 agencias: transacciones de caja, esperas, depósitos, retiros y ventas. | 9,378 | 14 |
| 08 | Retail | `retail_ventas_tienda` | Líneas de ticket de 15 tiendas (hiper, súper y express) en 7 categorías. | 32,494 | 19 |
| 09 | Retail | `retail_inventario_diario` | Inventario diario por tienda y SKU (abril–junio 2026) con entradas, ventas, ajustes y cobertura. | 22,567 | 15 |
| 10 | Retail | `retail_ecommerce_pedidos` | Pedidos online con cupones, transportista, estado y tiempos de entrega. | 12,127 | 20 |
| 11 | Retail | `retail_devoluciones` | Devoluciones en tienda con motivo, estado del producto y reembolso. | 4,008 | 14 |
| 12 | Retail | `retail_programa_fidelizacion` | Miembros del programa de lealtad con nivel, puntos, gasto y actividad de 12 meses. | 8,016 | 15 |
| 13 | Retail | `retail_campanas_marketing` | Desempeño diario de 8 campañas en 6 canales: impresiones, clics, conversiones, inversión e ingresos. | 1,010 | 11 |
| 14 | Retail | `retail_resenas_productos` | Reseñas de clientes con calificación 1–5, título y comentario. | 8,016 | 13 |
| 15 | Alimentos | `alimentos_produccion_planta` | Producción por planta, línea y turno con paros, rechazos, OEE y energía. | 5,457 | 16 |
| 16 | Alimentos | `alimentos_calidad_lotes` | Análisis de laboratorio (microbiológicos, fisicoquímicos, peso y sensorial) por lote. | 6,012 | 16 |
| 17 | Alimentos | `alimentos_distribucion_entregas` | Entregas desde 5 centros de distribución con retrasos, devoluciones, temperatura y flete. | 12,036 | 18 |
| 18 | Alimentos | `alimentos_ventas_canal` | Facturación por canal (supermercados, tiendas de barrio, HoReCa, mayoristas, e-commerce). | 25,075 | 17 |
| 19 | Alimentos | `alimentos_compras_materia_prima` | Órdenes de compra de materias primas con proveedor, país, incoterm, calidad y retrasos. | 6,012 | 15 |
| 20 | Alimentos | `alimentos_cadena_frio_mermas` | Mermas por vencimiento, ruptura de cadena de frío y daños, con temperatura registrada. | 10,020 | 15 |

## Calidad de datos (a propósito)
Como en la vida real, los archivos traen pequeñas imperfecciones para que Silver tenga algo que limpiar:
- Alrededor de 0.2 %–0.4 % de **filas duplicadas** exactas (deduplicar por la llave de cada fuente).
- **Valores nulos** en algunas columnas opcionales.
- Pequeñas inconsistencias de texto: espacios al final y mayúsculas en una columna categórica por fuente.

## Detalle por fuente
### 01 · `banca_transacciones_tarjeta`
Compras con tarjeta de débito y crédito en comercios, e-commerce, ATM y contactless. **Grano:** 1 fila = 1 transacción. **Filas:** 30,120.

**Columnas:** `transaccion_id`, `fecha_hora`, `tarjeta_id`, `cliente_id`, `nombre_cliente`, `segmento`, `tipo_tarjeta`, `comercio`, `categoria_comercio`, `ciudad`, `pais`, `canal`, `monto_usd`, `moneda`, `estado`, `motivo_rechazo`

**Preguntas para el agente:**
- ¿Cuánto se gasta por categoría de comercio y tipo de tarjeta?
- ¿Qué motivos de rechazo son más frecuentes por canal?
- ¿Cómo evoluciona el monto aprobado por mes y segmento?

### 02 · `banca_prestamos`
Cartera de préstamos desembolsados (personal, hipotecario, vehicular, pyme, libre inversión). **Grano:** 1 fila = 1 préstamo. **Filas:** 6,012.

**Columnas:** `prestamo_id`, `cliente_id`, `nombre_cliente`, `producto`, `agencia`, `ciudad`, `fecha_desembolso`, `monto_desembolsado`, `plazo_meses`, `tasa_anual_pct`, `cuota_mensual_usd`, `saldo_capital`, `estado`, `ejecutivo_cuenta`, `score_crediticio`, `ingreso_mensual`

**Preguntas para el agente:**
- ¿Cuál es el monto desembolsado por producto y agencia?
- ¿Cuál es la tasa promedio ponderada por producto?
- ¿Qué ejecutivos colocan más cartera?

### 03 · `banca_cartera_morosidad`
Foto de la cartera vigente al 30-jun-2026 con días de mora, provisión y gestión de cobranza. **Grano:** 1 fila = 1 préstamo vigente. **Filas:** 4,698.

**Columnas:** `prestamo_id`, `cliente_id`, `producto`, `fecha_corte`, `dias_mora`, `bucket_mora`, `saldo_vencido`, `saldo_total`, `provision_usd`, `gestor_cobranza`, `ultima_gestion_fecha`, `canal_gestion`, `resultado_gestion`

**Preguntas para el agente:**
- ¿Cuál es el índice de morosidad por producto?
- ¿Cuánta provisión se requiere por tramo de mora?
- ¿Qué canal de cobranza logra más promesas de pago?

### 04 · `banca_cuentas_movimientos`
Movimientos de cuentas de ahorro, corriente y nómina (depósitos, retiros, transferencias, pagos). **Grano:** 1 fila = 1 movimiento. **Filas:** 30,120.

**Columnas:** `movimiento_id`, `fecha`, `cuenta_id`, `cliente_id`, `tipo_cuenta`, `tipo_movimiento`, `canal`, `monto_usd`, `signo`, `agencia`, `saldo_posterior_usd`

**Preguntas para el agente:**
- ¿Qué canal concentra más retiros y depósitos?
- ¿Cuál es el flujo neto mensual por tipo de cuenta?
- ¿Cuánto se cobra en comisiones por mes?

### 05 · `banca_atencion_clientes`
Casos de servicio al cliente (reclamos, consultas, solicitudes) con SLA y satisfacción. **Grano:** 1 fila = 1 caso. **Filas:** 8,024.

**Columnas:** `caso_id`, `fecha_apertura`, `fecha_cierre`, `cliente_id`, `segmento`, `canal`, `tipo_caso`, `categoria`, `prioridad`, `estado`, `agente`, `tiempo_resolucion_horas`, `sla_cumplido`, `csat`

**Preguntas para el agente:**
- ¿Cuál es el % de cumplimiento de SLA por categoría?
- ¿Qué canal tiene mejor CSAT?
- ¿Cuánto tarda en promedio resolver un reclamo por prioridad?

### 06 · `banca_alertas_fraude`
Alertas del motor antifraude sobre transacciones con tarjeta y su resultado de revisión. **Grano:** 1 fila = 1 alerta. **Filas:** 5,010.

**Columnas:** `alerta_id`, `fecha_hora`, `transaccion_id`, `cliente_id`, `regla_disparada`, `score_riesgo`, `monto_usd`, `pais_origen`, `canal`, `analista`, `resultado`, `tiempo_revision_min`, `monto_recuperado_usd`

**Preguntas para el agente:**
- ¿Qué regla genera más fraude confirmado?
- ¿Cuál es la tasa de falsos positivos por canal?
- ¿Cuánto dinero se recuperó por mes?

### 07 · `banca_operaciones_agencias`
Operación diaria de 20 agencias: transacciones de caja, esperas, depósitos, retiros y ventas. **Grano:** 1 fila = 1 agencia por día hábil. **Filas:** 9,378.

**Columnas:** `fecha`, `agencia_id`, `agencia`, `ciudad`, `pais`, `transacciones_caja`, `clientes_atendidos`, `tiempo_espera_prom_min`, `depositos_usd`, `retiros_usd`, `aperturas_cuenta`, `ventas_tarjetas`, `ventas_prestamos`, `personal_turno`

**Preguntas para el agente:**
- ¿Qué agencias tienen mayor tiempo de espera?
- ¿Cuál es la venta de tarjetas y préstamos por agencia?
- ¿Qué días del mes hay más transacciones?

### 08 · `retail_ventas_tienda`
Líneas de ticket de 15 tiendas (hiper, súper y express) en 7 categorías. **Grano:** 1 fila = 1 línea de ticket. **Filas:** 32,494.

**Columnas:** `ticket_id`, `linea`, `fecha_hora`, `tienda_id`, `tienda`, `ciudad`, `formato_tienda`, `cajero`, `sku`, `producto`, `categoria`, `subcategoria`, `marca`, `cantidad`, `precio_unitario`, `descuento_pct`, `total_linea`, `medio_pago`, `cliente_fidelizado_id`

**Preguntas para el agente:**
- ¿Cuáles son las ventas por tienda, categoría y día?
- ¿Cuál es el ticket promedio por formato de tienda?
- ¿Qué medio de pago predomina por ciudad?

### 09 · `retail_inventario_diario`
Inventario diario por tienda y SKU (abril–junio 2026) con entradas, ventas, ajustes y cobertura. **Grano:** 1 fila = 1 tienda × SKU × día. **Filas:** 22,567.

**Columnas:** `fecha`, `tienda_id`, `tienda`, `sku`, `producto`, `categoria`, `stock_inicial`, `entradas`, `ventas_unidades`, `ajustes`, `stock_final`, `stock_minimo`, `costo_unitario`, `dias_cobertura`, `quiebre_stock`

**Preguntas para el agente:**
- ¿Qué SKU tienen más quiebres de stock?
- ¿Cuántos días de cobertura tiene cada categoría?
- ¿Qué tienda tiene más ajustes de inventario?

### 10 · `retail_ecommerce_pedidos`
Pedidos online con cupones, transportista, estado y tiempos de entrega. **Grano:** 1 fila = 1 línea de pedido. **Filas:** 12,127.

**Columnas:** `pedido_id`, `linea`, `fecha_pedido`, `cliente_id`, `nombre_cliente`, `ciudad_entrega`, `canal_origen`, `sku`, `producto`, `categoria`, `cantidad`, `precio_unitario`, `cupon`, `costo_envio`, `total_linea`, `metodo_pago`, `estado_pedido`, `transportista`, `fecha_entrega`, `dias_entrega`

**Preguntas para el agente:**
- ¿Qué canal de origen genera más ventas?
- ¿Cuál es el tiempo de entrega por transportista?
- ¿Cuál es la tasa de cancelación y devolución por categoría?

### 11 · `retail_devoluciones`
Devoluciones en tienda con motivo, estado del producto y reembolso. **Grano:** 1 fila = 1 devolución. **Filas:** 4,008.

**Columnas:** `devolucion_id`, `fecha_devolucion`, `ticket_id`, `tienda`, `ciudad`, `sku`, `producto`, `categoria`, `cantidad`, `monto_reembolsado`, `motivo`, `estado_producto`, `metodo_reembolso`, `dias_desde_compra`

**Preguntas para el agente:**
- ¿Cuáles son los principales motivos de devolución por categoría?
- ¿Cuánto se reembolsa por tienda y mes?
- ¿En cuántos días se devuelve un producto en promedio?

### 12 · `retail_programa_fidelizacion`
Miembros del programa de lealtad con nivel, puntos, gasto y actividad de 12 meses. **Grano:** 1 fila = 1 miembro. **Filas:** 8,016.

**Columnas:** `cliente_id`, `nombre`, `genero`, `fecha_nacimiento`, `ciudad`, `fecha_inscripcion`, `nivel`, `puntos_acumulados`, `puntos_canjeados`, `compras_12m`, `gasto_12m_usd`, `ultima_compra`, `canal_preferido`, `acepta_marketing`, `correo`

**Preguntas para el agente:**
- ¿Cuánto gasta cada nivel de fidelización?
- ¿Cuántos miembros están inactivos hace más de 180 días?
- ¿Qué ciudad concentra más miembros Platino?

### 13 · `retail_campanas_marketing`
Desempeño diario de 8 campañas en 6 canales: impresiones, clics, conversiones, inversión e ingresos. **Grano:** 1 fila = 1 campaña × canal × día. **Filas:** 1,010.

**Columnas:** `campana_id`, `campana`, `canal`, `fecha`, `categoria_objetivo`, `segmento`, `impresiones`, `clics`, `conversiones`, `inversion_usd`, `ingresos_atribuidos_usd`

**Preguntas para el agente:**
- ¿Qué canal tiene mejor retorno (ROAS)?
- ¿Cuál es el costo por conversión por campaña?
- ¿Qué campaña genera más ingresos atribuidos?

### 14 · `retail_resenas_productos`
Reseñas de clientes con calificación 1–5, título y comentario. **Grano:** 1 fila = 1 reseña. **Filas:** 8,016.

**Columnas:** `resena_id`, `fecha`, `sku`, `producto`, `categoria`, `marca`, `cliente_id`, `calificacion`, `titulo`, `comentario`, `recomienda`, `compra_verificada`, `canal_compra`

**Preguntas para el agente:**
- ¿Qué categorías tienen la peor calificación promedio?
- ¿Qué marcas tienen mayor % de recomendación?
- ¿Cómo evoluciona la calificación por mes?

### 15 · `alimentos_produccion_planta`
Producción por planta, línea y turno con paros, rechazos, OEE y energía. **Grano:** 1 fila = 1 línea × turno × día. **Filas:** 5,457.

**Columnas:** `fecha`, `planta`, `linea_produccion`, `turno`, `sku`, `producto`, `lote`, `unidades_planificadas`, `unidades_producidas`, `unidades_rechazadas`, `horas_programadas`, `horas_paro`, `causa_paro`, `oee_pct`, `consumo_energia_kwh`, `operarios`

**Preguntas para el agente:**
- ¿Cuál es el OEE promedio por planta y línea?
- ¿Cuáles son las principales causas de paro y cuántas horas restan?
- ¿Qué producto tiene más unidades rechazadas?

### 16 · `alimentos_calidad_lotes`
Análisis de laboratorio (microbiológicos, fisicoquímicos, peso y sensorial) por lote. **Grano:** 1 fila = 1 análisis. **Filas:** 6,012.

**Columnas:** `analisis_id`, `fecha_analisis`, `planta`, `sku`, `producto`, `lote`, `tipo_analisis`, `parametro`, `valor_medido`, `limite_min`, `limite_max`, `unidad`, `resultado`, `analista`, `temperatura_proceso_c`, `accion_correctiva`

**Preguntas para el agente:**
- ¿Cuál es el % de no conformidad por planta y tipo de análisis?
- ¿Qué acciones correctivas se aplican más?
- ¿Qué productos tienen más lotes no conformes?

### 17 · `alimentos_distribucion_entregas`
Entregas desde 5 centros de distribución con retrasos, devoluciones, temperatura y flete. **Grano:** 1 fila = 1 entrega. **Filas:** 12,036.

**Columnas:** `entrega_id`, `fecha_programada`, `centro_distribucion`, `ruta`, `vehiculo`, `conductor`, `cliente`, `ciudad`, `cajas_entregadas`, `cajas_devueltas`, `peso_kg`, `distancia_km`, `tiempo_ruta_min`, `minutos_retraso`, `temperatura_promedio_c`, `entrega_a_tiempo`, `incidencia`, `costo_flete_usd`

**Preguntas para el agente:**
- ¿Cuál es el % de entregas a tiempo por centro?
- ¿Qué incidencias son más comunes?
- ¿Cuál es el costo de flete por kilómetro y ruta?

### 18 · `alimentos_ventas_canal`
Facturación por canal (supermercados, tiendas de barrio, HoReCa, mayoristas, e-commerce). **Grano:** 1 fila = 1 línea de factura. **Filas:** 25,075.

**Columnas:** `factura_id`, `fecha`, `canal`, `cliente`, `ciudad`, `vendedor`, `sku`, `producto`, `linea_producto`, `presentacion`, `cajas`, `precio_caja_usd`, `descuento_pct`, `total_usd`, `costo_usd`, `condicion_pago`, `estado_cobro`

**Preguntas para el agente:**
- ¿Cuál es el margen por canal y línea de producto?
- ¿Qué vendedores venden más?
- ¿Cuánto está vencido por cobrar y en qué canal?

### 19 · `alimentos_compras_materia_prima`
Órdenes de compra de materias primas con proveedor, país, incoterm, calidad y retrasos. **Grano:** 1 fila = 1 orden de compra. **Filas:** 6,012.

**Columnas:** `orden_compra_id`, `fecha_orden`, `fecha_recepcion`, `proveedor`, `pais_origen`, `categoria`, `materia_prima`, `cantidad`, `unidad`, `precio_unitario_usd`, `total_usd`, `incoterm`, `lote_proveedor`, `estado_calidad`, `dias_retraso`

**Preguntas para el agente:**
- ¿Cuánto se compra por categoría y país de origen?
- ¿Qué proveedores tienen más retrasos?
- ¿Cómo varía el precio unitario por materia prima?

### 20 · `alimentos_cadena_frio_mermas`
Mermas por vencimiento, ruptura de cadena de frío y daños, con temperatura registrada. **Grano:** 1 fila = 1 registro de merma. **Filas:** 10,020.

**Columnas:** `merma_id`, `fecha`, `centro`, `area`, `sku`, `producto`, `linea_producto`, `lote`, `causa_merma`, `unidades`, `costo_unitario_usd`, `costo_total_usd`, `temperatura_registrada_c`, `temperatura_max_permitida_c`, `responsable_registro`

**Preguntas para el agente:**
- ¿Cuál es el costo de merma por causa y centro?
- ¿En qué área ocurren más rupturas de cadena de frío?
- ¿Qué líneas de producto pierden más dinero?

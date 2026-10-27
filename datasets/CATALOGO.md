# Datasets del laboratorio

45 fuentes sintéticas organizadas por rubro. Cada fuente es **una carpeta con un único archivo CSV consolidado** (UTF-8, con encabezado, fechas ISO).
El nombre de la carpeta es el nombre de la FUENTE que se usa en el prompt y en el esquema `<INI>_<FUENTE>`.

Stage destino: `@COFFEE_BRONZE.LANDING.STG_DATASETS/<fuente>/<fuente>.csv`  ·  File format: `COFFEE_BRONZE.LANDING.FF_CSV`

Los datos son ficticios y no corresponden a ninguna empresa real. Cubren de enero 2025 a junio 2026 (salvo donde se indica).
Las fuentes de banca y retail operan en Centroamérica y Colombia y están en USD; las demás están pensadas para Guatemala y usan quetzales (GTQ) cuando el nombre de la columna termina en `_gtq`.

**¿No ves tu rubro?** Cada participante puede elegir la fuente más cercana a su industria: seguros, banca, agroindustria, energía, telecom, agua, sector público, petróleo, textil, automotriz, educación, tecnología, cemento, pinturas, avícola, alimentos o retail.

## Catálogo por rubro

### Banca y financiero
*Aplica a: bancos, financieras y bancos hipotecarios.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 01 | `banca_transacciones_tarjeta` | Compras con tarjeta de débito y crédito en comercios, e-commerce, ATM y contactless. | 30,120 | 16 |
| 02 | `banca_prestamos` | Cartera de préstamos desembolsados (personal, hipotecario, vehicular, pyme, libre inversión). | 6,012 | 16 |
| 03 | `banca_cartera_morosidad` | Foto de la cartera vigente al 30-jun-2026 con días de mora, provisión y gestión de cobranza. | 4,698 | 13 |
| 04 | `banca_cuentas_movimientos` | Movimientos de cuentas de ahorro, corriente y nómina (depósitos, retiros, transferencias, pagos). | 30,120 | 11 |
| 05 | `banca_atencion_clientes` | Casos de servicio al cliente (reclamos, consultas, solicitudes) con SLA y satisfacción. | 8,024 | 14 |
| 06 | `banca_alertas_fraude` | Alertas del motor antifraude sobre transacciones con tarjeta y su resultado de revisión. | 5,010 | 13 |
| 07 | `banca_operaciones_agencias` | Operación diaria de 20 agencias: transacciones de caja, esperas, depósitos, retiros y ventas. | 9,378 | 14 |

### Retail y comercio
*Aplica a: comercio minorista, supermercados y e-commerce.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 08 | `retail_ventas_tienda` | Líneas de ticket de 15 tiendas (hiper, súper y express) en 7 categorías. | 32,494 | 19 |
| 09 | `retail_inventario_diario` | Inventario diario por tienda y SKU (abril–junio 2026) con entradas, ventas, ajustes y cobertura. | 22,567 | 15 |
| 10 | `retail_ecommerce_pedidos` | Pedidos online con cupones, transportista, estado y tiempos de entrega. | 12,127 | 20 |
| 11 | `retail_devoluciones` | Devoluciones en tienda con motivo, estado del producto y reembolso. | 4,008 | 14 |
| 12 | `retail_programa_fidelizacion` | Miembros del programa de lealtad con nivel, puntos, gasto y actividad de 12 meses. | 8,016 | 15 |
| 13 | `retail_campanas_marketing` | Desempeño diario de 8 campañas en 6 canales: impresiones, clics, conversiones, inversión e ingresos. | 1,010 | 11 |
| 14 | `retail_resenas_productos` | Reseñas de clientes con calificación 1–5, título y comentario. | 8,016 | 13 |

### Alimentos y bebidas
*Aplica a: manufactura y distribución de alimentos.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 15 | `alimentos_produccion_planta` | Producción por planta, línea y turno con paros, rechazos, OEE y energía. | 5,457 | 16 |
| 16 | `alimentos_calidad_lotes` | Análisis de laboratorio (microbiológicos, fisicoquímicos, peso y sensorial) por lote. | 6,012 | 16 |
| 17 | `alimentos_distribucion_entregas` | Entregas desde 5 centros de distribución con retrasos, devoluciones, temperatura y flete. | 12,036 | 18 |
| 18 | `alimentos_ventas_canal` | Facturación por canal (supermercados, tiendas de barrio, HoReCa, mayoristas, e-commerce). | 25,075 | 17 |
| 19 | `alimentos_compras_materia_prima` | Órdenes de compra de materias primas con proveedor, país, incoterm, calidad y retrasos. | 6,012 | 15 |
| 20 | `alimentos_cadena_frio_mermas` | Mermas por vencimiento, ruptura de cadena de frío y daños, con temperatura registrada. | 10,020 | 15 |

### Seguros
*Aplica a: aseguradoras, corredores, consultoras de riesgos y beneficios, y software para seguros.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 21 | `seguros_polizas_emision` | Emisión de pólizas por ramo (vida, gastos médicos, autos, incendio, RC, transporte, accidentes) con suma asegurada, prima, canal y comisión. | 12,036 | 19 |
| 22 | `seguros_siniestros` | Siniestros reportados con monto reclamado, reservado y pagado, estado, motivo de rechazo y sospecha de fraude. | 5,015 | 15 |
| 23 | `seguros_cobranza_primas` | Recibos de primas por cuota con fecha de pago, medio de pago, atraso y cancelación por falta de pago. | 10,441 | 15 |

### Cemento y construcción
*Aplica a: cemento, concreto y materiales de construcción.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 24 | `cemento_despachos_ventas` | Despachos de cemento y concreto a distribuidores, ferreterías, constructoras y proyectos, con flete y tiempos de carga. | 20,060 | 16 |
| 25 | `cemento_produccion_planta` | Producción diaria por horno: clínker, cemento molido, paros, combustible alternativo, energía y emisiones de CO2. | 3,282 | 13 |

### Manufactura industrial (pinturas)
*Aplica a: manufactura y distribución de pinturas y recubrimientos.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 26 | `pinturas_ventas_distribucion` | Ventas de pinturas y recubrimientos (arquitectónica, industrial, impermeabilizantes, madera, automotriz) por canal y presentación. | 18,054 | 16 |

### Agroindustria
*Aplica a: palma, banano, azúcar, café y distribución de agroinsumos.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 27 | `agro_cosecha_fincas` | Cosechas por finca y lote de palma, banano, plátano, caña, hule y café, con rendimiento, calidad, costo y destino. | 9,027 | 15 |
| 28 | `agro_zafra_ingenio` | Operación diaria de zafra por ingenio: caña molida, azúcar, sacarosa, paros, bagazo, energía exportada, melaza y etanol. | 862 | 12 |
| 29 | `agro_ventas_insumos` | Ventas de fertilizantes, agroquímicos, semillas y nutrición y salud animal a agricultores, fincas, cooperativas y distribuidores. | 14,042 | 17 |

### Avícola
*Aplica a: producción y procesamiento de pollo.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 30 | `avicola_granjas_produccion` | Lotes de pollo de engorde por granja y galpón: mortalidad, peso final, conversión alimenticia, costo de alimento y rendimiento a canal. | 3,006 | 18 |

### Energía eléctrica
*Aplica a: distribución y generación de energía.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 31 | `energia_facturacion_consumo` | Facturación mensual de energía por cliente: consumo kWh, demanda, tarifa, subsidio, medidor y estado de pago. | 30,060 | 16 |
| 32 | `energia_interrupciones_servicio` | Interrupciones del servicio eléctrico por circuito y subestación: causa, duración, clientes afectados y energía no suministrada. | 8,016 | 14 |

### Telecomunicaciones
*Aplica a: operadores móviles, fibra y datos.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 33 | `telecom_suscriptores` | Base de suscriptores (prepago, pospago, empresarial, hogar) con plan, ARPU, consumo, reclamos y bajas con motivo. | 10,020 | 17 |
| 34 | `telecom_incidencias_red` | Incidencias de red móvil y fibra: tecnología, severidad, clientes afectados, duración, causa raíz, SLA y costo de reparación. | 8,016 | 14 |

### Agua y servicios municipales
*Aplica a: empresas municipales de agua y saneamiento.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 35 | `agua_facturacion_consumo` | Facturación mensual de agua por cuenta: consumo m3, tarifa, tipo de medidor, lecturas anómalas y mora. | 22,044 | 13 |
| 36 | `agua_reclamos_fugas` | Reclamos de servicio de agua y alcantarillado (fugas, falta de agua, baja presión, cobros) con tiempos de resolución y pérdida estimada. | 7,014 | 13 |

### Sector público y tributario
*Aplica a: administración tributaria y aduanas.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 37 | `gobierno_recaudacion_tributaria` | Declaraciones y pagos de impuestos (IVA, ISR, ISO, timbres, circulación) por tipo de contribuyente y actividad económica. | 25,050 | 17 |
| 38 | `gobierno_aduanas_importaciones` | Declaraciones aduaneras por aduana y régimen: valor CIF, arancel, IVA de importación, canal de selectividad y tiempo de despacho. | 15,030 | 17 |

### Petróleo y gas
*Aplica a: exploración y producción de hidrocarburos.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 39 | `petroleo_produccion_pozos` | Producción diaria por pozo: petróleo, agua, gas, corte de agua, presión, horas de operación y causas de paro. | 13,663 | 14 |

### Textil y confección
*Aplica a: hilandería, tejeduría y confección.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 40 | `textil_produccion_ordenes` | Órdenes de producción textil por proceso (hilandería, tejeduría, tintorería, acabado, confección) con defectos, merma y consumo de agua y energía. | 7,021 | 19 |

### Automotriz y distribución
*Aplica a: distribución de vehículos, repuestos y lubricantes.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 41 | `automotriz_ventas_repuestos` | Ventas de lubricantes, repuestos, llantas, accesorios y servicios de taller por sucursal y tipo de cliente. | 16,048 | 15 |

### Educación superior
*Aplica a: universidades.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 42 | `educacion_matricula_rendimiento` | Matrícula y rendimiento académico por estudiante y curso: facultad, carrera, jornada, nota final, asistencia, becas y retiros. | 24,072 | 17 |

### Tecnología
*Aplica a: software, consultoría TI y ciberseguridad.*

| # | Fuente (carpeta) | Qué contiene | Filas | Cols |
|---|---|---|---|---|
| 43 | `ti_eventos_ciberseguridad` | Eventos de seguridad (SIEM, EDR, firewall, correo, IAM) con tipo, severidad, táctica MITRE, tiempos de detección y respuesta, y falsos positivos. | 20,060 | 17 |
| 44 | `software_suscripciones_saas` | Suscripciones de un producto de software por cuenta y mes: plan, usuarios licenciados y activos, MRR, NPS, tickets y estado (activa, en riesgo, cancelada). | 4,828 | 16 |
| 45 | `servicios_ti_proyectos_horas` | Registro de horas de consultores en proyectos de TI (integración, datos, ciberseguridad, cloud, soporte): tarifa, facturación y aprobación. | 16,048 | 14 |

## Calidad de datos (a propósito)
Como en la vida real, los archivos traen pequeñas imperfecciones para que Silver tenga algo que limpiar:
- Alrededor de 0.2 %–0.4 % de **filas duplicadas** exactas (deduplicar por la llave de cada fuente).
- **Valores nulos** en algunas columnas opcionales.
- Pequeñas inconsistencias de texto: espacios al final y mayúsculas en una columna categórica por fuente.

## Detalle por fuente
### 01 · `banca_transacciones_tarjeta` — Banca y financiero
Compras con tarjeta de débito y crédito en comercios, e-commerce, ATM y contactless. **Grano:** 1 fila = 1 transacción. **Filas:** 30,120.

**Columnas:** `transaccion_id`, `fecha_hora`, `tarjeta_id`, `cliente_id`, `nombre_cliente`, `segmento`, `tipo_tarjeta`, `comercio`, `categoria_comercio`, `ciudad`, `pais`, `canal`, `monto_usd`, `moneda`, `estado`, `motivo_rechazo`

**Preguntas para el agente:**
- ¿Cuánto se gasta por categoría de comercio y tipo de tarjeta?
- ¿Qué motivos de rechazo son más frecuentes por canal?
- ¿Cómo evoluciona el monto aprobado por mes y segmento?

### 02 · `banca_prestamos` — Banca y financiero
Cartera de préstamos desembolsados (personal, hipotecario, vehicular, pyme, libre inversión). **Grano:** 1 fila = 1 préstamo. **Filas:** 6,012.

**Columnas:** `prestamo_id`, `cliente_id`, `nombre_cliente`, `producto`, `agencia`, `ciudad`, `fecha_desembolso`, `monto_desembolsado`, `plazo_meses`, `tasa_anual_pct`, `cuota_mensual_usd`, `saldo_capital`, `estado`, `ejecutivo_cuenta`, `score_crediticio`, `ingreso_mensual`

**Preguntas para el agente:**
- ¿Cuál es el monto desembolsado por producto y agencia?
- ¿Cuál es la tasa promedio ponderada por producto?
- ¿Qué ejecutivos colocan más cartera?

### 03 · `banca_cartera_morosidad` — Banca y financiero
Foto de la cartera vigente al 30-jun-2026 con días de mora, provisión y gestión de cobranza. **Grano:** 1 fila = 1 préstamo vigente. **Filas:** 4,698.

**Columnas:** `prestamo_id`, `cliente_id`, `producto`, `fecha_corte`, `dias_mora`, `bucket_mora`, `saldo_vencido`, `saldo_total`, `provision_usd`, `gestor_cobranza`, `ultima_gestion_fecha`, `canal_gestion`, `resultado_gestion`

**Preguntas para el agente:**
- ¿Cuál es el índice de morosidad por producto?
- ¿Cuánta provisión se requiere por tramo de mora?
- ¿Qué canal de cobranza logra más promesas de pago?

### 04 · `banca_cuentas_movimientos` — Banca y financiero
Movimientos de cuentas de ahorro, corriente y nómina (depósitos, retiros, transferencias, pagos). **Grano:** 1 fila = 1 movimiento. **Filas:** 30,120.

**Columnas:** `movimiento_id`, `fecha`, `cuenta_id`, `cliente_id`, `tipo_cuenta`, `tipo_movimiento`, `canal`, `monto_usd`, `signo`, `agencia`, `saldo_posterior_usd`

**Preguntas para el agente:**
- ¿Qué canal concentra más retiros y depósitos?
- ¿Cuál es el flujo neto mensual por tipo de cuenta?
- ¿Cuánto se cobra en comisiones por mes?

### 05 · `banca_atencion_clientes` — Banca y financiero
Casos de servicio al cliente (reclamos, consultas, solicitudes) con SLA y satisfacción. **Grano:** 1 fila = 1 caso. **Filas:** 8,024.

**Columnas:** `caso_id`, `fecha_apertura`, `fecha_cierre`, `cliente_id`, `segmento`, `canal`, `tipo_caso`, `categoria`, `prioridad`, `estado`, `agente`, `tiempo_resolucion_horas`, `sla_cumplido`, `csat`

**Preguntas para el agente:**
- ¿Cuál es el % de cumplimiento de SLA por categoría?
- ¿Qué canal tiene mejor CSAT?
- ¿Cuánto tarda en promedio resolver un reclamo por prioridad?

### 06 · `banca_alertas_fraude` — Banca y financiero
Alertas del motor antifraude sobre transacciones con tarjeta y su resultado de revisión. **Grano:** 1 fila = 1 alerta. **Filas:** 5,010.

**Columnas:** `alerta_id`, `fecha_hora`, `transaccion_id`, `cliente_id`, `regla_disparada`, `score_riesgo`, `monto_usd`, `pais_origen`, `canal`, `analista`, `resultado`, `tiempo_revision_min`, `monto_recuperado_usd`

**Preguntas para el agente:**
- ¿Qué regla genera más fraude confirmado?
- ¿Cuál es la tasa de falsos positivos por canal?
- ¿Cuánto dinero se recuperó por mes?

### 07 · `banca_operaciones_agencias` — Banca y financiero
Operación diaria de 20 agencias: transacciones de caja, esperas, depósitos, retiros y ventas. **Grano:** 1 fila = 1 agencia por día hábil. **Filas:** 9,378.

**Columnas:** `fecha`, `agencia_id`, `agencia`, `ciudad`, `pais`, `transacciones_caja`, `clientes_atendidos`, `tiempo_espera_prom_min`, `depositos_usd`, `retiros_usd`, `aperturas_cuenta`, `ventas_tarjetas`, `ventas_prestamos`, `personal_turno`

**Preguntas para el agente:**
- ¿Qué agencias tienen mayor tiempo de espera?
- ¿Cuál es la venta de tarjetas y préstamos por agencia?
- ¿Qué días del mes hay más transacciones?

### 08 · `retail_ventas_tienda` — Retail y comercio
Líneas de ticket de 15 tiendas (hiper, súper y express) en 7 categorías. **Grano:** 1 fila = 1 línea de ticket. **Filas:** 32,494.

**Columnas:** `ticket_id`, `linea`, `fecha_hora`, `tienda_id`, `tienda`, `ciudad`, `formato_tienda`, `cajero`, `sku`, `producto`, `categoria`, `subcategoria`, `marca`, `cantidad`, `precio_unitario`, `descuento_pct`, `total_linea`, `medio_pago`, `cliente_fidelizado_id`

**Preguntas para el agente:**
- ¿Cuáles son las ventas por tienda, categoría y día?
- ¿Cuál es el ticket promedio por formato de tienda?
- ¿Qué medio de pago predomina por ciudad?

### 09 · `retail_inventario_diario` — Retail y comercio
Inventario diario por tienda y SKU (abril–junio 2026) con entradas, ventas, ajustes y cobertura. **Grano:** 1 fila = 1 tienda × SKU × día. **Filas:** 22,567.

**Columnas:** `fecha`, `tienda_id`, `tienda`, `sku`, `producto`, `categoria`, `stock_inicial`, `entradas`, `ventas_unidades`, `ajustes`, `stock_final`, `stock_minimo`, `costo_unitario`, `dias_cobertura`, `quiebre_stock`

**Preguntas para el agente:**
- ¿Qué SKU tienen más quiebres de stock?
- ¿Cuántos días de cobertura tiene cada categoría?
- ¿Qué tienda tiene más ajustes de inventario?

### 10 · `retail_ecommerce_pedidos` — Retail y comercio
Pedidos online con cupones, transportista, estado y tiempos de entrega. **Grano:** 1 fila = 1 línea de pedido. **Filas:** 12,127.

**Columnas:** `pedido_id`, `linea`, `fecha_pedido`, `cliente_id`, `nombre_cliente`, `ciudad_entrega`, `canal_origen`, `sku`, `producto`, `categoria`, `cantidad`, `precio_unitario`, `cupon`, `costo_envio`, `total_linea`, `metodo_pago`, `estado_pedido`, `transportista`, `fecha_entrega`, `dias_entrega`

**Preguntas para el agente:**
- ¿Qué canal de origen genera más ventas?
- ¿Cuál es el tiempo de entrega por transportista?
- ¿Cuál es la tasa de cancelación y devolución por categoría?

### 11 · `retail_devoluciones` — Retail y comercio
Devoluciones en tienda con motivo, estado del producto y reembolso. **Grano:** 1 fila = 1 devolución. **Filas:** 4,008.

**Columnas:** `devolucion_id`, `fecha_devolucion`, `ticket_id`, `tienda`, `ciudad`, `sku`, `producto`, `categoria`, `cantidad`, `monto_reembolsado`, `motivo`, `estado_producto`, `metodo_reembolso`, `dias_desde_compra`

**Preguntas para el agente:**
- ¿Cuáles son los principales motivos de devolución por categoría?
- ¿Cuánto se reembolsa por tienda y mes?
- ¿En cuántos días se devuelve un producto en promedio?

### 12 · `retail_programa_fidelizacion` — Retail y comercio
Miembros del programa de lealtad con nivel, puntos, gasto y actividad de 12 meses. **Grano:** 1 fila = 1 miembro. **Filas:** 8,016.

**Columnas:** `cliente_id`, `nombre`, `genero`, `fecha_nacimiento`, `ciudad`, `fecha_inscripcion`, `nivel`, `puntos_acumulados`, `puntos_canjeados`, `compras_12m`, `gasto_12m_usd`, `ultima_compra`, `canal_preferido`, `acepta_marketing`, `correo`

**Preguntas para el agente:**
- ¿Cuánto gasta cada nivel de fidelización?
- ¿Cuántos miembros están inactivos hace más de 180 días?
- ¿Qué ciudad concentra más miembros Platino?

### 13 · `retail_campanas_marketing` — Retail y comercio
Desempeño diario de 8 campañas en 6 canales: impresiones, clics, conversiones, inversión e ingresos. **Grano:** 1 fila = 1 campaña × canal × día. **Filas:** 1,010.

**Columnas:** `campana_id`, `campana`, `canal`, `fecha`, `categoria_objetivo`, `segmento`, `impresiones`, `clics`, `conversiones`, `inversion_usd`, `ingresos_atribuidos_usd`

**Preguntas para el agente:**
- ¿Qué canal tiene mejor retorno (ROAS)?
- ¿Cuál es el costo por conversión por campaña?
- ¿Qué campaña genera más ingresos atribuidos?

### 14 · `retail_resenas_productos` — Retail y comercio
Reseñas de clientes con calificación 1–5, título y comentario. **Grano:** 1 fila = 1 reseña. **Filas:** 8,016.

**Columnas:** `resena_id`, `fecha`, `sku`, `producto`, `categoria`, `marca`, `cliente_id`, `calificacion`, `titulo`, `comentario`, `recomienda`, `compra_verificada`, `canal_compra`

**Preguntas para el agente:**
- ¿Qué categorías tienen la peor calificación promedio?
- ¿Qué marcas tienen mayor % de recomendación?
- ¿Cómo evoluciona la calificación por mes?

### 15 · `alimentos_produccion_planta` — Alimentos y bebidas
Producción por planta, línea y turno con paros, rechazos, OEE y energía. **Grano:** 1 fila = 1 línea × turno × día. **Filas:** 5,457.

**Columnas:** `fecha`, `planta`, `linea_produccion`, `turno`, `sku`, `producto`, `lote`, `unidades_planificadas`, `unidades_producidas`, `unidades_rechazadas`, `horas_programadas`, `horas_paro`, `causa_paro`, `oee_pct`, `consumo_energia_kwh`, `operarios`

**Preguntas para el agente:**
- ¿Cuál es el OEE promedio por planta y línea?
- ¿Cuáles son las principales causas de paro y cuántas horas restan?
- ¿Qué producto tiene más unidades rechazadas?

### 16 · `alimentos_calidad_lotes` — Alimentos y bebidas
Análisis de laboratorio (microbiológicos, fisicoquímicos, peso y sensorial) por lote. **Grano:** 1 fila = 1 análisis. **Filas:** 6,012.

**Columnas:** `analisis_id`, `fecha_analisis`, `planta`, `sku`, `producto`, `lote`, `tipo_analisis`, `parametro`, `valor_medido`, `limite_min`, `limite_max`, `unidad`, `resultado`, `analista`, `temperatura_proceso_c`, `accion_correctiva`

**Preguntas para el agente:**
- ¿Cuál es el % de no conformidad por planta y tipo de análisis?
- ¿Qué acciones correctivas se aplican más?
- ¿Qué productos tienen más lotes no conformes?

### 17 · `alimentos_distribucion_entregas` — Alimentos y bebidas
Entregas desde 5 centros de distribución con retrasos, devoluciones, temperatura y flete. **Grano:** 1 fila = 1 entrega. **Filas:** 12,036.

**Columnas:** `entrega_id`, `fecha_programada`, `centro_distribucion`, `ruta`, `vehiculo`, `conductor`, `cliente`, `ciudad`, `cajas_entregadas`, `cajas_devueltas`, `peso_kg`, `distancia_km`, `tiempo_ruta_min`, `minutos_retraso`, `temperatura_promedio_c`, `entrega_a_tiempo`, `incidencia`, `costo_flete_usd`

**Preguntas para el agente:**
- ¿Cuál es el % de entregas a tiempo por centro?
- ¿Qué incidencias son más comunes?
- ¿Cuál es el costo de flete por kilómetro y ruta?

### 18 · `alimentos_ventas_canal` — Alimentos y bebidas
Facturación por canal (supermercados, tiendas de barrio, HoReCa, mayoristas, e-commerce). **Grano:** 1 fila = 1 línea de factura. **Filas:** 25,075.

**Columnas:** `factura_id`, `fecha`, `canal`, `cliente`, `ciudad`, `vendedor`, `sku`, `producto`, `linea_producto`, `presentacion`, `cajas`, `precio_caja_usd`, `descuento_pct`, `total_usd`, `costo_usd`, `condicion_pago`, `estado_cobro`

**Preguntas para el agente:**
- ¿Cuál es el margen por canal y línea de producto?
- ¿Qué vendedores venden más?
- ¿Cuánto está vencido por cobrar y en qué canal?

### 19 · `alimentos_compras_materia_prima` — Alimentos y bebidas
Órdenes de compra de materias primas con proveedor, país, incoterm, calidad y retrasos. **Grano:** 1 fila = 1 orden de compra. **Filas:** 6,012.

**Columnas:** `orden_compra_id`, `fecha_orden`, `fecha_recepcion`, `proveedor`, `pais_origen`, `categoria`, `materia_prima`, `cantidad`, `unidad`, `precio_unitario_usd`, `total_usd`, `incoterm`, `lote_proveedor`, `estado_calidad`, `dias_retraso`

**Preguntas para el agente:**
- ¿Cuánto se compra por categoría y país de origen?
- ¿Qué proveedores tienen más retrasos?
- ¿Cómo varía el precio unitario por materia prima?

### 20 · `alimentos_cadena_frio_mermas` — Alimentos y bebidas
Mermas por vencimiento, ruptura de cadena de frío y daños, con temperatura registrada. **Grano:** 1 fila = 1 registro de merma. **Filas:** 10,020.

**Columnas:** `merma_id`, `fecha`, `centro`, `area`, `sku`, `producto`, `linea_producto`, `lote`, `causa_merma`, `unidades`, `costo_unitario_usd`, `costo_total_usd`, `temperatura_registrada_c`, `temperatura_max_permitida_c`, `responsable_registro`

**Preguntas para el agente:**
- ¿Cuál es el costo de merma por causa y centro?
- ¿En qué área ocurren más rupturas de cadena de frío?
- ¿Qué líneas de producto pierden más dinero?

### 21 · `seguros_polizas_emision` — Seguros
Emisión de pólizas por ramo (vida, gastos médicos, autos, incendio, RC, transporte, accidentes) con suma asegurada, prima, canal y comisión. **Grano:** 1 fila = 1 póliza. **Filas:** 12,036.

**Columnas:** `poliza_id`, `fecha_emision`, `vigencia_inicio`, `vigencia_fin`, `ramo`, `producto`, `canal_venta`, `agente`, `asegurado_id`, `tipo_asegurado`, `departamento`, `suma_asegurada_gtq`, `prima_anual_gtq`, `forma_pago`, `deducible_gtq`, `estado_poliza`, `tipo_negocio`, `comision_pct`, `edad_asegurado`

**Preguntas para el agente:**
- ¿Cuánta prima se emitió por ramo y canal de venta?
- ¿Qué agentes generan más prima nueva vs. renovación?
- ¿Cuál es la tasa de cancelación por ramo y departamento?

### 22 · `seguros_siniestros` — Seguros
Siniestros reportados con monto reclamado, reservado y pagado, estado, motivo de rechazo y sospecha de fraude. **Grano:** 1 fila = 1 siniestro. **Filas:** 5,015.

**Columnas:** `siniestro_id`, `poliza_id`, `fecha_ocurrencia`, `fecha_reporte`, `ramo`, `cobertura`, `departamento`, `monto_reclamado_gtq`, `monto_reservado_gtq`, `monto_pagado_gtq`, `estado_siniestro`, `dias_resolucion`, `ajustador`, `sospecha_fraude`, `motivo_rechazo`

**Preguntas para el agente:**
- ¿Cuál es la siniestralidad (pagado / prima) por ramo?
- ¿Cuántos días tarda en resolverse un siniestro por cobertura?
- ¿Qué motivos de rechazo son más frecuentes?

### 23 · `seguros_cobranza_primas` — Seguros
Recibos de primas por cuota con fecha de pago, medio de pago, atraso y cancelación por falta de pago. **Grano:** 1 fila = 1 recibo (cuota). **Filas:** 10,441.

**Columnas:** `recibo_id`, `poliza_id`, `numero_cuota`, `total_cuotas`, `fecha_vencimiento`, `fecha_pago`, `ramo`, `forma_pago`, `monto_prima_gtq`, `monto_pagado_gtq`, `estado_cobro`, `medio_pago`, `dias_atraso`, `gestor_cobro`, `canal_venta`

**Preguntas para el agente:**
- ¿Qué porcentaje de las primas está vencido por forma de pago?
- ¿Qué medio de pago tiene menos atraso?
- ¿Cuánto se cancela por falta de pago por ramo?

### 24 · `cemento_despachos_ventas` — Cemento y construcción
Despachos de cemento y concreto a distribuidores, ferreterías, constructoras y proyectos, con flete y tiempos de carga. **Grano:** 1 fila = 1 despacho. **Filas:** 20,060.

**Columnas:** `despacho_id`, `fecha`, `planta_origen`, `producto`, `presentacion`, `tipo_cliente`, `cliente`, `departamento_destino`, `cantidad_ton`, `precio_ton_gtq`, `total_gtq`, `flete_gtq`, `distancia_km`, `camion_placa`, `tiempo_carga_min`, `estado_entrega`

**Preguntas para el agente:**
- ¿Cuántas toneladas se despachan por planta y tipo de cliente?
- ¿Cuál es el flete promedio por tonelada y departamento?
- ¿Qué porcentaje de entregas sale con demora?

### 25 · `cemento_produccion_planta` — Cemento y construcción
Producción diaria por horno: clínker, cemento molido, paros, combustible alternativo, energía y emisiones de CO2. **Grano:** 1 fila = 1 horno por día. **Filas:** 3,282.

**Columnas:** `fecha`, `planta`, `horno`, `clinker_ton`, `cemento_molido_ton`, `horas_operacion`, `horas_paro`, `causa_paro`, `consumo_combustible_gj`, `combustible_alternativo_pct`, `consumo_energia_kwh`, `emisiones_co2_ton`, `factor_clinker_pct`

**Preguntas para el agente:**
- ¿Cuál es el factor clínker y el consumo de energía por planta?
- ¿Qué causas de paro suman más horas?
- ¿Cómo evolucionan las emisiones de CO2 por tonelada de cemento?

### 26 · `pinturas_ventas_distribucion` — Manufactura industrial (pinturas)
Ventas de pinturas y recubrimientos (arquitectónica, industrial, impermeabilizantes, madera, automotriz) por canal y presentación. **Grano:** 1 fila = 1 línea de factura. **Filas:** 18,054.

**Columnas:** `factura_id`, `fecha`, `canal`, `cliente`, `departamento`, `vendedor`, `producto`, `linea_producto`, `presentacion`, `color`, `unidades`, `precio_unitario_gtq`, `descuento_pct`, `costo_unitario_gtq`, `condicion_pago`, `total_gtq`

**Preguntas para el agente:**
- ¿Cuál es el margen por línea de producto y canal?
- ¿Qué colores y presentaciones se venden más?
- ¿Cuánto vende cada vendedor por departamento?

### 27 · `agro_cosecha_fincas` — Agroindustria
Cosechas por finca y lote de palma, banano, plátano, caña, hule y café, con rendimiento, calidad, costo y destino. **Grano:** 1 fila = 1 cosecha de un lote. **Filas:** 9,027.

**Columnas:** `registro_id`, `fecha_cosecha`, `finca`, `cultivo`, `departamento`, `lote`, `area_ha`, `toneladas_cosechadas`, `rendimiento_ton_ha_por_corte`, `calidad`, `cuadrilla`, `clima`, `costo_cosecha_gtq`, `precio_referencia_usd_ton`, `destino`

**Preguntas para el agente:**
- ¿Cuál es el rendimiento por hectárea de cada cultivo y departamento?
- ¿Qué fincas tienen mayor porcentaje de rechazo?
- ¿Cuál es el costo de cosecha por tonelada?

### 28 · `agro_zafra_ingenio` — Agroindustria
Operación diaria de zafra por ingenio: caña molida, azúcar, sacarosa, paros, bagazo, energía exportada, melaza y etanol. **Grano:** 1 fila = 1 ingenio por día de zafra. **Filas:** 862.

**Columnas:** `fecha`, `ingenio`, `cana_molida_ton`, `azucar_producida_qq`, `sacarosa_pct`, `horas_molienda`, `horas_paro`, `causa_paro`, `bagazo_ton`, `energia_exportada_mwh`, `melaza_ton`, `etanol_litros`

**Preguntas para el agente:**
- ¿Cuál es el rendimiento de azúcar por tonelada de caña y por ingenio?
- ¿Cuántas horas de paro hubo y por qué causa?
- ¿Cuánta energía se exportó por mes?

### 29 · `agro_ventas_insumos` — Agroindustria
Ventas de fertilizantes, agroquímicos, semillas y nutrición y salud animal a agricultores, fincas, cooperativas y distribuidores. **Grano:** 1 fila = 1 línea de factura. **Filas:** 14,042.

**Columnas:** `factura_id`, `fecha`, `tipo_cliente`, `cliente`, `departamento`, `vendedor`, `producto`, `categoria`, `cultivo_objetivo`, `presentacion`, `cantidad`, `precio_unitario_gtq`, `descuento_pct`, `condicion_pago`, `estado_cobro`, `total_gtq`, `costo_gtq`

**Preguntas para el agente:**
- ¿Qué categoría de insumos se vende más en la época lluviosa?
- ¿Cuál es el margen por tipo de cliente?
- ¿Cuánta cartera está vencida y en qué departamento?

### 30 · `avicola_granjas_produccion` — Avícola
Lotes de pollo de engorde por granja y galpón: mortalidad, peso final, conversión alimenticia, costo de alimento y rendimiento a canal. **Grano:** 1 fila = 1 lote. **Filas:** 3,006.

**Columnas:** `lote_id`, `fecha_ingreso`, `fecha_salida`, `granja`, `galpon`, `departamento`, `pollitos_ingresados`, `mortalidad_pct`, `aves_beneficiadas`, `dias_ciclo`, `peso_final_kg`, `conversion_alimenticia`, `consumo_alimento_kg`, `costo_alimento_gtq`, `rendimiento_canal_pct`, `decomisos_pct`, `veterinario`, `estado_sanitario`

**Preguntas para el agente:**
- ¿Qué granjas tienen la mejor conversión alimenticia?
- ¿Cómo se relaciona la mortalidad con los días de ciclo?
- ¿Cuál es el costo de alimento por kilo producido?

### 31 · `energia_facturacion_consumo` — Energía eléctrica
Facturación mensual de energía por cliente: consumo kWh, demanda, tarifa, subsidio, medidor y estado de pago. **Grano:** 1 fila = 1 factura (cliente-mes). **Filas:** 30,060.

**Columnas:** `factura_id`, `periodo`, `cliente_id`, `tipo_cliente`, `tarifa`, `departamento`, `municipio`, `tipo_medidor`, `kwh_consumidos`, `demanda_kw`, `lectura_estimada`, `monto_facturado_gtq`, `subsidio_gtq`, `fecha_vencimiento`, `estado_pago`, `dias_mora`

**Preguntas para el agente:**
- ¿Cuál es el consumo y la facturación por tipo de cliente y departamento?
- ¿Cuántos clientes están en mora y por cuántos días?
- ¿Qué porcentaje de lecturas es estimado según el tipo de medidor?

### 32 · `energia_interrupciones_servicio` — Energía eléctrica
Interrupciones del servicio eléctrico por circuito y subestación: causa, duración, clientes afectados y energía no suministrada. **Grano:** 1 fila = 1 interrupción. **Filas:** 8,016.

**Columnas:** `evento_id`, `fecha_inicio`, `fecha_fin`, `duracion_min`, `tipo_interrupcion`, `causa`, `circuito`, `subestacion`, `departamento`, `clientes_afectados`, `kva_afectado`, `cuadrilla`, `tiempo_respuesta_min`, `energia_no_suministrada_kwh`

**Preguntas para el agente:**
- ¿Cuál es el tiempo promedio de interrupción por departamento (tipo SAIDI)?
- ¿Qué causas afectan a más clientes?
- ¿Cuánto tarda la respuesta de la cuadrilla en interrupciones no programadas?

### 33 · `telecom_suscriptores` — Telecomunicaciones
Base de suscriptores (prepago, pospago, empresarial, hogar) con plan, ARPU, consumo, reclamos y bajas con motivo. **Grano:** 1 fila = 1 suscriptor. **Filas:** 10,020.

**Columnas:** `suscriptor_id`, `fecha_alta`, `segmento`, `plan`, `canal_venta`, `departamento`, `edad`, `genero`, `equipo_marca`, `arpu_mensual_gtq`, `datos_gb_mes`, `minutos_mes`, `antiguedad_meses`, `reclamos_90d`, `estado`, `fecha_baja`, `motivo_baja`

**Preguntas para el agente:**
- ¿Cuál es la tasa de bajas (churn) por segmento y plan?
- ¿Qué motivos de baja son más frecuentes?
- ¿Cuál es el ARPU por canal de venta y antigüedad?

### 34 · `telecom_incidencias_red` — Telecomunicaciones
Incidencias de red móvil y fibra: tecnología, severidad, clientes afectados, duración, causa raíz, SLA y costo de reparación. **Grano:** 1 fila = 1 incidencia. **Filas:** 8,016.

**Columnas:** `incidencia_id`, `fecha_hora`, `tipo_incidencia`, `tecnologia`, `sitio_id`, `departamento`, `severidad`, `clientes_afectados`, `duracion_min`, `causa_raiz`, `tiempo_asignacion_min`, `cuadrilla`, `sla_cumplido`, `costo_reparacion_gtq`

**Preguntas para el agente:**
- ¿Qué tecnología tiene más minutos de caída?
- ¿Cuál es el cumplimiento de SLA por severidad?
- ¿Cuál es la causa raíz más costosa?

### 35 · `agua_facturacion_consumo` — Agua y servicios municipales
Facturación mensual de agua por cuenta: consumo m3, tarifa, tipo de medidor, lecturas anómalas y mora. **Grano:** 1 fila = 1 factura (cuenta-mes). **Filas:** 22,044.

**Columnas:** `factura_id`, `periodo`, `cuenta_id`, `tipo_usuario`, `zona`, `tipo_medidor`, `m3_consumidos`, `tarifa_gtq_m3`, `cargo_fijo_gtq`, `monto_facturado_gtq`, `lectura_anomala`, `estado_pago`, `dias_mora`

**Preguntas para el agente:**
- ¿Cuál es el consumo promedio por zona y tipo de usuario?
- ¿Cuánta facturación está en mora?
- ¿Qué zonas tienen más lecturas anómalas?

### 36 · `agua_reclamos_fugas` — Agua y servicios municipales
Reclamos de servicio de agua y alcantarillado (fugas, falta de agua, baja presión, cobros) con tiempos de resolución y pérdida estimada. **Grano:** 1 fila = 1 ticket. **Filas:** 7,014.

**Columnas:** `ticket_id`, `fecha_reporte`, `fecha_cierre`, `tipo_reclamo`, `zona`, `canal`, `prioridad`, `estado`, `cuadrilla`, `tiempo_resolucion_horas`, `perdida_estimada_m3`, `costo_reparacion_gtq`, `sla_cumplido`

**Preguntas para el agente:**
- ¿Cuánta agua se pierde por fugas por zona?
- ¿Cuál es el cumplimiento de SLA por tipo de reclamo?
- ¿Qué canal recibe más reclamos?

### 37 · `gobierno_recaudacion_tributaria` — Sector público y tributario
Declaraciones y pagos de impuestos (IVA, ISR, ISO, timbres, circulación) por tipo de contribuyente y actividad económica. **Grano:** 1 fila = 1 declaración. **Filas:** 25,050.

**Columnas:** `declaracion_id`, `contribuyente_id`, `fecha_presentacion`, `periodo_fiscal`, `impuesto`, `tipo_contribuyente`, `actividad_economica`, `departamento`, `base_imponible_gtq`, `impuesto_determinado_gtq`, `credito_fiscal_gtq`, `monto_pagado_gtq`, `fecha_vencimiento`, `presentada_extemporanea`, `multa_mora_gtq`, `medio_presentacion`, `estado`

**Preguntas para el agente:**
- ¿Cuánto se recauda por impuesto y mes?
- ¿Qué porcentaje de declaraciones se presenta extemporáneamente y cuánta multa genera?
- ¿Qué actividades económicas aportan más ISR?

### 38 · `gobierno_aduanas_importaciones` — Sector público y tributario
Declaraciones aduaneras por aduana y régimen: valor CIF, arancel, IVA de importación, canal de selectividad y tiempo de despacho. **Grano:** 1 fila = 1 declaración aduanera. **Filas:** 15,030.

**Columnas:** `declaracion_aduanera_id`, `fecha`, `aduana`, `regimen`, `pais_origen_destino`, `categoria_producto`, `partida_arancelaria`, `valor_cif_usd`, `peso_kg`, `contenedores`, `arancel_pct`, `derechos_arancelarios_usd`, `iva_importacion_usd`, `canal_selectividad`, `tiempo_despacho_horas`, `agente_aduanal`, `incidencia`

**Preguntas para el agente:**
- ¿Cuáles son los derechos arancelarios recaudados por aduana?
- ¿Cuánto tarda el despacho según el canal de selectividad?
- ¿Qué categorías de producto concentran más valor importado?

### 39 · `petroleo_produccion_pozos` — Petróleo y gas
Producción diaria por pozo: petróleo, agua, gas, corte de agua, presión, horas de operación y causas de paro. **Grano:** 1 fila = 1 pozo por día. **Filas:** 13,663.

**Columnas:** `fecha`, `pozo_id`, `campo`, `tipo_levantamiento`, `departamento`, `petroleo_bbl`, `agua_bbl`, `gas_mscf`, `corte_agua_pct`, `presion_cabezal_psi`, `temperatura_c`, `horas_operacion`, `estado_pozo`, `causa_paro`

**Preguntas para el agente:**
- ¿Cuál es la producción de petróleo por campo y mes?
- ¿Qué pozos tienen mayor corte de agua?
- ¿Cuántas horas se pierden por paros y por qué causa?

### 40 · `textil_produccion_ordenes` — Textil y confección
Órdenes de producción textil por proceso (hilandería, tejeduría, tintorería, acabado, confección) con defectos, merma y consumo de agua y energía. **Grano:** 1 fila = 1 orden de producción. **Filas:** 7,021.

**Columnas:** `orden_id`, `fecha_inicio`, `fecha_fin`, `proceso`, `producto`, `tipo_cliente`, `maquina`, `turno`, `color`, `unidad`, `cantidad_planificada`, `cantidad_producida`, `cantidad_segunda`, `defectos_por_100`, `merma_pct`, `consumo_agua_m3`, `consumo_energia_kwh`, `eficiencia_pct`, `entrega_a_tiempo`

**Preguntas para el agente:**
- ¿Cuál es la eficiencia y la merma por proceso?
- ¿Qué máquinas generan más material de segunda?
- ¿Cuánta agua consume la tintorería por metro?

### 41 · `automotriz_ventas_repuestos` — Automotriz y distribución
Ventas de lubricantes, repuestos, llantas, accesorios y servicios de taller por sucursal y tipo de cliente. **Grano:** 1 fila = 1 línea de factura. **Filas:** 16,048.

**Columnas:** `factura_id`, `fecha`, `sucursal`, `tipo_venta`, `producto`, `categoria`, `marca`, `tipo_cliente`, `vendedor`, `cantidad`, `precio_unitario_gtq`, `descuento_pct`, `costo_unitario_gtq`, `forma_pago`, `total_gtq`

**Preguntas para el agente:**
- ¿Cuál es el margen por categoría y sucursal?
- ¿Qué productos venden más los talleres independientes?
- ¿Cuánto aportan los servicios de taller a la venta total?

### 42 · `educacion_matricula_rendimiento` — Educación superior
Matrícula y rendimiento académico por estudiante y curso: facultad, carrera, jornada, nota final, asistencia, becas y retiros. **Grano:** 1 fila = 1 estudiante en 1 curso. **Filas:** 24,072.

**Columnas:** `registro_id`, `ciclo`, `semestre`, `facultad`, `carrera`, `curso`, `estudiante_id`, `genero`, `edad`, `departamento_origen`, `jornada`, `anio_carrera`, `nota_final`, `asistencia_pct`, `repitente`, `beca`, `estado_curso`

**Preguntas para el agente:**
- ¿Cuál es el porcentaje de aprobación por facultad y jornada?
- ¿Cómo se relaciona la asistencia con la nota?
- ¿Qué cursos tienen más retiros?

### 43 · `ti_eventos_ciberseguridad` — Tecnología
Eventos de seguridad (SIEM, EDR, firewall, correo, IAM) con tipo, severidad, táctica MITRE, tiempos de detección y respuesta, y falsos positivos. **Grano:** 1 fila = 1 evento. **Filas:** 20,060.

**Columnas:** `evento_id`, `fecha_hora`, `fuente`, `tipo_evento`, `tactica_mitre`, `severidad`, `ip_origen`, `pais_origen`, `tipo_activo`, `activo_afectado`, `usuario_afectado`, `accion_tomada`, `analista`, `tiempo_deteccion_min`, `tiempo_respuesta_min`, `falso_positivo`, `estado_incidente`

**Preguntas para el agente:**
- ¿Qué tipos de evento son más críticos y de qué países provienen?
- ¿Cuál es el tiempo medio de detección y de respuesta por severidad?
- ¿Qué fuente genera más falsos positivos?

### 44 · `software_suscripciones_saas` — Tecnología
Suscripciones de un producto de software por cuenta y mes: plan, usuarios licenciados y activos, MRR, NPS, tickets y estado (activa, en riesgo, cancelada). **Grano:** 1 fila = 1 cuenta por mes. **Filas:** 4,828.

**Columnas:** `registro_id`, `mes`, `cuenta_id`, `pais`, `industria_cliente`, `plan`, `modulo`, `canal_adquisicion`, `fecha_inicio`, `usuarios_licenciados`, `usuarios_activos`, `mrr_usd`, `tickets_soporte`, `nps`, `uso_funcionalidades_pct`, `estado`

**Preguntas para el agente:**
- ¿Cómo evoluciona el MRR por plan y país?
- ¿Qué cuentas están en riesgo de cancelar?
- ¿Cómo se relaciona el uso de funcionalidades con el NPS?

### 45 · `servicios_ti_proyectos_horas` — Tecnología
Registro de horas de consultores en proyectos de TI (integración, datos, ciberseguridad, cloud, soporte): tarifa, facturación y aprobación. **Grano:** 1 fila = 1 registro de horas. **Filas:** 16,048.

**Columnas:** `registro_id`, `fecha`, `consultor`, `nivel`, `proyecto_id`, `proyecto`, `sector_cliente`, `tipo_servicio`, `horas`, `tarifa_hora_usd`, `facturable`, `monto_usd`, `modalidad`, `estado_aprobacion`

**Preguntas para el agente:**
- ¿Cuál es la utilización facturable por consultor y nivel?
- ¿Qué proyectos consumen más horas no facturables?
- ¿Cuánto se factura por tipo de servicio y sector del cliente?

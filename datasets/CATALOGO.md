# Catálogo de fuentes — `@COFFEE_BRONZE.LANDING.STG_DATASETS`

Cada carpeta del stage es una **FUENTE** (nombre de esquema `<INI>_<FUENTE>`, ej. `GG_SUPERSTORE`).
Origen: datasets públicos de Kaggle. Todos son CSV con encabezado, delimitador `,`.

## Resumen
| Carpeta (FUENTE) | Archivo(s) | Filas | Periodo | Contexto de negocio |
|---|---|---|---|---|
| `superstore/` (`SUPERSTORE`) | `Sample_-_Superstore.csv` | 9.994 | 2014–2017 | Retail en EE. UU.: pedidos de clientes con envío, producto, ventas, descuento y utilidad |
| `supermercado/` (`SUPERMERCADO`) | `annex1.csv` catálogo · `annex2.csv` ventas · `annex3.csv` precio mayorista · `annex4.csv` merma | 251 · 878.503 · 55.982 · 251 | 2020-07 a 2023-06 | Supermercado de verduras en China (RMB/kg): ventas por transacción, costos mayoristas diarios y % de merma por producto |
| `rrhh/` (`RRHH`) | `WA_Fn-UseC_-HR-Employee-Attrition.csv` | 1.470 | Foto única | Empleados (IBM, ficticio): perfil, puesto, salario, satisfacción y si renunció (`Attrition`) |
| `churn/` (`CHURN`) | `WA_Fn-UseC_-Telco-Customer-Churn.csv` | 7.043 | Foto única | Clientes de telecomunicaciones: servicios contratados, contrato, cargos y si se dieron de baja (`Churn`) |
| `airbnb/` (`AIRBNB`) | `AB_NYC_2019.csv` | ~48.900 | Reseñas 2011–2019 | Anuncios de Airbnb en Nueva York: anfitrión, barrio, tipo de habitación, precio, reseñas y disponibilidad |

## Columnas por archivo
| Archivo | Columnas |
|---|---|
| `superstore/Sample_-_Superstore.csv` | Row ID, Order ID, Order Date, Ship Date, Ship Mode, Customer ID, Customer Name, Segment, Country, City, State, Postal Code, Region, Product ID, Category, Sub-Category, Product Name, Sales, Quantity, Discount, Profit |
| `supermercado/annex1.csv` | Item Code, Item Name, Category Code, Category Name |
| `supermercado/annex2.csv` | Date, Time, Item Code, Quantity Sold (kilo), Unit Selling Price (RMB/kg), Sale or Return, Discount (Yes/No) |
| `supermercado/annex3.csv` | Date, Item Code, Wholesale Price (RMB/kg) |
| `supermercado/annex4.csv` | Item Code, Item Name, Loss Rate (%) |
| `rrhh/WA_Fn-UseC_-HR-Employee-Attrition.csv` | Age, Attrition, BusinessTravel, DailyRate, Department, DistanceFromHome, Education, EducationField, EmployeeCount, EmployeeNumber, EnvironmentSatisfaction, Gender, HourlyRate, JobInvolvement, JobLevel, JobRole, JobSatisfaction, MaritalStatus, MonthlyIncome, MonthlyRate, NumCompaniesWorked, Over18, OverTime, PercentSalaryHike, PerformanceRating, RelationshipSatisfaction, StandardHours, StockOptionLevel, TotalWorkingYears, TrainingTimesLastYear, WorkLifeBalance, YearsAtCompany, YearsInCurrentRole, YearsSinceLastPromotion, YearsWithCurrManager |
| `churn/WA_Fn-UseC_-Telco-Customer-Churn.csv` | customerID, gender, SeniorCitizen, Partner, Dependents, tenure, PhoneService, MultipleLines, InternetService, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies, Contract, PaperlessBilling, PaymentMethod, MonthlyCharges, TotalCharges, Churn |
| `airbnb/AB_NYC_2019.csv` | id, name, host_id, host_name, neighbourhood_group, neighbourhood, latitude, longitude, room_type, price, minimum_nights, number_of_reviews, last_review, reviews_per_month, calculated_host_listings_count, availability_365 |

## Cuidados al cargar (Bronze/Silver)
- **superstore:** codificación Latin-1 (usar `ENCODING = 'ISO-8859-1'`); fechas `M/D/YYYY` → `TRY_TO_DATE(x, 'MM/DD/YYYY')`.
- **supermercado:** `annex2` es grande (~52 MB); nombres de columna con espacios y paréntesis → renombrar en STG_; `annex4` empieza con BOM.
- **rrhh:** el archivo empieza con BOM (la primera columna puede leerse como `﻿Age`); `EmployeeCount`, `Over18` y `StandardHours` son constantes.
- **churn:** `TotalCharges` es texto con valores en blanco → `TRY_TO_NUMBER(NULLIF(TRIM(x), ''))`.
- **airbnb:** textos con comas y saltos de línea → `FIELD_OPTIONALLY_ENCLOSED_BY = '"'`; `last_review` y `reviews_per_month` vacíos cuando no hay reseñas.

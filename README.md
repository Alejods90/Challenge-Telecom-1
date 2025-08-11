# Análisis de Datos de TelecomX

Este proyecto analiza los datos de cancelación de clientes (churn) de TelecomX, explorando la relación entre las características de los clientes y el comportamiento de cancelación.

---

## Objetivo del Proyecto

El objetivo principal de este proyecto es comprender los factores que influyen en la cancelación de clientes en TelecomX y visualizar los hallazgos clave.

---

## Fuente de Datos

Los datos utilizados en este análisis provienen de un archivo JSON llamado `TelecomX_Data.json`.

---

## Pasos del Análisis

1.  **Carga y Normalización de Datos**: Los datos JSON se cargaron y normalizaron usando `pandas.json_normalize` para aplanar la estructura anidada en un DataFrame.
2.  **Limpieza de Datos**:
    * Se verificaron los valores faltantes.
    * Se identificaron y manejaron las cadenas de texto vacías en las columnas 'Churn' y 'account.Charges.Total', filtrando las filas con valores de 'Churn' vacíos y convirtiendo 'account.Charges.Total' a un tipo numérico con coerción para los errores.
3.  **Ingeniería de Características (Feature Engineering)**: Se creó una nueva columna 'Charges_daily' dividiendo 'account.Charges.Monthly' entre 30.
4.  **Renombrado de Columnas**: Las columnas con nombres anidados (p. ej., 'customer.gender') se renombraron a nombres más simples y legibles (p. ej., 'Gender').
5.  **Conversión de Tipos de Datos**: Las columnas de tipo objeto con valores 'Yes'/'No' se convirtieron a tipo entero (1/0). La columna 'Total' se convirtió a numérica.
6.  **Estadísticas Descriptivas**: Se generaron estadísticas de resumen para las columnas numéricas para comprender su distribución.
7.  **Análisis Exploratorio de Datos (EDA)**:
    * **Distribución del Churn**: Se creó un gráfico circular para visualizar la distribución general de la cancelación.
    * **Análisis de Variables Categóricas**: Se generaron gráficos de barras para mostrar la distribución de la cancelación a través de diversas características categóricas como 'Gender', 'Partner', 'Dependents', 'PhoneService', 'MultipleLines', 'InternetService', 'OnlineSecurity', 'OnlineBackup', 'DeviceProtection', 'TechSupport', 'StreamingTV', 'StreamingMovies', 'Contract', 'PaperlessBilling' y 'PaymentMethod'.
    * **Análisis de Variables Numéricas**: Se utilizaron diagramas de caja (box plots) para visualizar la relación entre la cancelación y características numéricas como 'Tenure', 'Monthly' y 'Total'.
    * **Análisis de Adultos Mayores (Senior Citizen)**: Se analizó y visualizó específicamente la relación entre el estado de 'SeniorCitizen' y la cancelación con un gráfico de barras.

---

## Hallazgos Clave

* Los clientes con servicio de internet **DSL o Fibra óptica** tienen una tasa de cancelación más alta en comparación con aquellos sin servicio de internet.
* Los clientes que carecen de **Seguridad en línea, Copia de seguridad en línea, Protección de dispositivos o Soporte técnico** tienden a cancelar más.
* Los clientes con un **contrato mes a mes** muestran una tasa de cancelación significativamente mayor que aquellos con contratos a más largo plazo.
* Los clientes que utilizan **facturación electrónica (PaperlessBilling)** tienen una tasa de cancelación más alta.
* Los diferentes **métodos de pago** exhiben tasas de cancelación variables.
* Los clientes que cancelaron tienen una **menor antigüedad (Tenure)** y, en general, **cargos mensuales más altos**.
* Los clientes que no cancelaron tienen **cargos totales más altos**, probablemente debido a una mayor antigüedad.
* Los **adultos mayores (Senior Citizens)** tienen una tasa de cancelación más alta (aprox. 41.6%) en comparación con los que no son adultos mayores (aprox. 23.6%).

---

## Próximos Pasos

* Se recomienda una investigación más a fondo de las razones detrás de la mayor tasa de cancelación entre los clientes con internet de fibra óptica, contratos mes a mes y facturación electrónica.
* Considerar la construcción de un modelo predictivo utilizando las características identificadas para pronosticar la cancelación de clientes e identificar a los clientes de alto riesgo para esfuerzos de retención dirigidos.

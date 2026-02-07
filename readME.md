# Alura Telecom X - Análisis Exploratorio de Datos (EDA)

## Propósitos del proyecto

Este proyecto tiene como objetivo analizar el comportamiento de los clientes de una empresa de telecomunicaciones y preparar los datos para el desarrollo de un modelo de Machine Learning orientado a la predicción de cancelación de clientes (Churn).

Se realiza un proceso completo de limpieza, normalización, estandarización y transformación de datos, con el fin de obtener un dataset consistente, claro y adecuado para análisis exploratorio y modelos predictivos.

## Objetivos

- Limpiar y normalizar datos provenientes de una fuente externa en formato JSON

- Estandarizar variables categóricas y binarias

- Crear variables derivadas para un análisis más detallado

- Preparar el dataset para modelos de Machine Learning

- Documentar claramente las transformaciones realizadas

El dataset contiene información a nivel cliente, incluyendo:

- Datos demográficos

- Servicios contratados

- Información de facturación y pagos

- Estado de cancelación del cliente (Churn)

Proceso de limpieza y transformación de datos
1️⃣ Normalización del archivo JSON

El archivo original contiene estructuras JSON anidadas.
Se utilizó pd.json_normalize() para convertir los datos en un DataFrame plano:

pd.json_normalize(df.to_dict(orient='records'))

2️⃣ Renombrado de columnas

Las columnas fueron renombradas para:

Mejorar la legibilidad

Mantener un formato consistente (snake_case)

Facilitar el análisis y el modelado

Ejemplo:

Columna original	Nueva columna
customer_SeniorCitizen	senior_65
customer_Partner	partner
customer_Dependents	dependents
customer_tenure	tenure_months
internet_StreamingTV	streaming_tv
3️⃣ Creación de variables derivadas

Se creó la columna daily_charge a partir del cargo mensual:

df_final['daily_charge'] = df_final['monthly_charge'] / 30


Esta variable permite analizar el costo diario del servicio por cliente.

4️⃣ Estandarización de variables binarias

Las variables binarias originalmente en texto fueron convertidas a valores numéricos para facilitar el análisis y el uso en modelos de Machine Learning.

Valor original		Valor numérico
     Yes			1
     No				0

Columnas transformadas:

- Churn

- partner

- dependents

- online_security

- tech_support

- streaming_tv

5️⃣ Manejo de valores faltantes

- Se detectaron valores vacíos ('') y se reemplazaron por NaN

- Los valores NaN en columnas binarias fueron imputados como 0

- Se realizó la conversión segura de tipos de datos

- df_final.replace('', np.nan, inplace=True)
- df_final[cols_binarias] = df_final[cols_binarias].fillna(0).astype(int)


## Herramientas utilizadas

- Python

- Pandas

- NumPy

- Jupyter Notebook
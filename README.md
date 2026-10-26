# ConnectaTel – Análisis de uso de servicios móviles

Este repositorio contiene el análisis del Proyecto 6: entender cómo usan los clientes de **ConnectaTel** (operaciones en México y Colombia) los servicios de llamadas y mensajes, detectar comportamientos atípicos y segmentar a los clientes para optimizar la oferta de planes.

## 🎯 Objetivo del proyecto

- Evaluar el comportamiento de uso de los clientes durante 2024.
- Detectar problemas de calidad de datos y valores atípicos.
- Segmentar a los clientes por edad y por nivel de uso.
- Traducir los hallazgos en recomendaciones comerciales.

## 📂 Contenido del repositorio

- `connectatel_analysis.ipynb`: notebook principal con todo el análisis.
- `README.md`: esta documentación.

## 📊 Datasets utilizados

| Archivo | Contenido | Tamaño |
|---|---|---|
| `plans.csv` | Planes actuales (precio, minutos, mensajes y GB incluidos, costo por extra) | 2 planes |
| `users_latam.csv` | Clientes: edad, ciudad, fecha de registro, plan y fecha de baja | 4,000 usuarios |
| `usage.csv` | Uso real: llamadas (duración) y mensajes (longitud), con fecha | 40,000 registros |

## 🔄 Etapas del análisis

1. **Carga y exploración:** estructura, tipos de datos y vista previa de los tres datasets.
2. **Calidad de datos:** conteo de nulos, detección de valores centinela (`-999`, `?`) y revisión de fechas fuera de rango.
3. **Limpieza básica:** reemplazo de centinelas, conversión de fechas y tratamiento de nulos según su causa.
4. **Estadísticas descriptivas:** métricas de uso por usuario (mensajes, llamadas y minutos) combinadas con los datos de clientes.
5. **Visualización y outliers:** histogramas por plan, boxplots y límites con el método IQR.
6. **Segmentación:** grupos por nivel de uso (Bajo, Medio, Alto) y por edad (Joven, Adulto, Adulto Mayor).
7. **Insight ejecutivo:** conclusiones y recomendaciones para el negocio.

## 🔍 Principales hallazgos

- **Calidad de datos:** 55 edades con el centinela `-999`, 565 usuarios sin ciudad válida (14.1%), 40 fechas de registro imposibles (año 2026) y 30 llamadas de exactamente 120 minutos, que sugieren un tope del sistema.
- **Segmentos de uso:** Uso medio 73.6%, Bajo uso 19.5% y Alto uso 6.95% de los usuarios.
- **Edad y plan no explican el uso:** el consumo es muy parecido entre grupos de edad y entre Basico y Premium.
- **Valor del cliente:** Premium es el 35% de los usuarios y aporta cerca del 53% del ingreso por cuota mensual (sin contar extras ni bajas).
- **Alto uso** concentra más bajas (14.0%) que el resto (≈ 11.5%), una señal a vigilar.

## ▶ Cómo abrir el notebook en Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU_USUARIO/telecom-analysis/blob/main/connectatel_analysis.ipynb)

También puedes abrir el archivo `.ipynb` en GitHub y usar el botón **Open in Colab**.

## 🧪 Cómo reproducir el análisis

1. Descarga los tres archivos CSV (`plans.csv`, `users_latam.csv` y `usage.csv`).
2. Colócalos en una carpeta `data/` o súbelos al entorno de Colab.
3. El notebook lee los datos desde la ruta `/datasets/` del entorno de la plataforma donde se desarrolló. Ajusta las rutas a tu ubicación, por ejemplo `pd.read_csv('data/plans.csv')`.
4. Ejecuta las celdas en orden, de arriba hacia abajo.

## 🛠️ Herramientas

Python, pandas, numpy, seaborn y matplotlib, en Jupyter Notebook.

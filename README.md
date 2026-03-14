# 🚕 Predicción de la Duración de Viajes de Taxi en Nueva York con Deep Learning

## 📌 Descripción del Proyecto

Este proyecto desarrolla un modelo de **Deep Learning** para predecir la duración de viajes de taxi en la ciudad de Nueva York utilizando datos reales de trayectos registrados por taxis.

El objetivo principal es construir un modelo capaz de estimar con precisión el **tiempo de duración de un viaje** a partir de variables espaciales, temporales y operativas como:

- coordenadas geográficas de origen y destino  
- distancia del viaje  
- número de pasajeros  
- hora del día  
- día de la semana  
- clusters geográficos de pickup y dropoff  

El proyecto incluye **Análisis Exploratorio de Datos (EDA)**, **Ingeniería de Características**, **Entrenamiento de Redes Neuronales Profundas** y **Evaluación del Modelo mediante métricas de regresión**.

---

## 📊 Dataset

El dataset utilizado corresponde a:

**New York City Taxi Trip Duration Dataset**

Incluye información sobre viajes de taxi en Nueva York como:

- `pickup_datetime`
- `pickup_longitude`
- `pickup_latitude`
- `dropoff_longitude`
- `dropoff_latitude`
- `passenger_count`
- `vendor_id`
- `store_and_fwd_flag`
- `trip_duration`

A partir de estas variables se generaron nuevas características espaciales y temporales para mejorar la capacidad predictiva del modelo.

---

## 🔎 Análisis Exploratorio de Datos (EDA)

Durante el análisis exploratorio se estudiaron las distribuciones y relaciones entre variables relevantes.

Principales análisis realizados:

- distribución de la duración de los viajes  
- transformación logarítmica de la variable objetivo  
- análisis de duración según hora del día  
- relación entre distancia recorrida y duración del viaje  
- distribución geográfica de puntos de recogida (pickup)

Estos análisis permitieron identificar patrones importantes del tráfico urbano en la ciudad de Nueva York.

---

## ⚙️ Ingeniería de Características

Se generaron nuevas variables con el objetivo de mejorar el rendimiento del modelo.

### Características espaciales

- `distance_km` → distancia geográfica entre origen y destino  
- `manhattan_distance` → distancia Manhattan  
- `bearing` → dirección del trayecto  
- `pickup_cluster`  
- `dropoff_cluster`

### Características temporales

- `hour`
- `dayofweek`
- `month`

Para capturar la naturaleza cíclica del tiempo se aplicaron transformaciones trigonométricas:

- `hour_sin`
- `hour_cos`
- `day_sin`
- `day_cos`

Además, la variable objetivo fue transformada utilizando:

```
log_trip_duration
```

Esto permitió reducir la asimetría en la distribución de los datos.

---

## 🧠 Arquitectura del Modelo

El modelo utilizado es una **Red Neuronal Profunda (Deep Neural Network)** implementada con **TensorFlow / Keras**.

Arquitectura:

```
Input Layer
   ↓
Dense (400) + ReLU
Batch Normalization
Dropout
   ↓
Dense (256) + ReLU
Batch Normalization
Dropout
   ↓
Dense (128) + ReLU
Batch Normalization
Dropout
   ↓
Dense (64) + ReLU
Batch Normalization
Dropout
   ↓
Dense (32) + ReLU
   ↓
Output Layer (Dense 1)
```

Técnicas utilizadas para mejorar el entrenamiento:

- **Batch Normalization**
- **Dropout**
- **Early Stopping**
- **Reduce Learning Rate on Plateau**

Estas técnicas ayudan a mejorar la estabilidad del entrenamiento y reducir el riesgo de **overfitting**.

---

## 📈 Evaluación del Modelo

El desempeño del modelo fue evaluado utilizando métricas de regresión:

- **MSE (Mean Squared Error)**  
- **RMSE (Root Mean Squared Error)**  
- **MAE (Mean Absolute Error)**  
- **R² (Coeficiente de Determinación)**  
- **Adjusted R²**

Estas métricas permiten medir la precisión del modelo en la predicción de la duración de los viajes.

---

## 📊 Visualizaciones

El proyecto incluye varias visualizaciones para analizar el comportamiento del dataset y el desempeño del modelo:

- distribución de duración de viajes
- distribución de `log_trip_duration`
- relación entre distancia y duración
- evolución del error durante el entrenamiento
- gráfico de valores **predichos vs reales**

---

## 🛠️ Tecnologías Utilizadas

- Python  
- TensorFlow / Keras  
- NumPy  
- Pandas  
- Scikit-learn  
- Matplotlib  
- Seaborn  

---

## 📂 Estructura del Proyecto

```
project/
│
├── data/
│   ├── train.csv
│
├── notebooks/
│   ├── taxi_trip_duration_analysis.ipynb
│
├── models/
│   ├── taxi_model.h5
│
├── figures/
│   ├── eda_plots
│
└── README.md
```

---

## 🚀 Cómo ejecutar el proyecto

### 1️⃣ Clonar el repositorio

```
git clone https://github.com/tuusuario/taxi-trip-duration-prediction.git
```

### 2️⃣ Instalar dependencias

```
pip install -r requirements.txt
```

### 3️⃣ Ejecutar el notebook

Abrir el archivo:

```
taxi_trip_duration_analysis.ipynb
```

en **Jupyter Notebook** o **Google Colab**.

---

## 📚 Aplicaciones

Los modelos de predicción de duración de viajes pueden utilizarse en:

- aplicaciones de transporte (Uber, Lyft)
- planificación de rutas
- estimación de tiempo de llegada (ETA)
- análisis de movilidad urbana
- sistemas de transporte inteligente

---

## 👨‍💻 Autores
- Angel Gutierrez Gutierrez
- Luz Alizon Mamani Mena
- Roni Edwin Oyardo Acuña

Proyecto desarrollado como parte de un trabajo académico en **Machine Learning y Deep Learning aplicado al análisis de datos de movilidad urbana**.

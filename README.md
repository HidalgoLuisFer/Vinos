

 # Proyecto: Análisis de Datos de Vinos y Sistema de Recomendación

 # Objetivos del Proyecto

El objetivo principal de este proyecto es:

* Proporcionar una comprensión profunda de los factores que influyen en la calidad y el precio de los vinos.
* Desarrollar herramientas útiles para los amantes del vino, como un sistema de recomendación y un clasificador de sentimientos en reseñas.

## Aplicaciones de los Resultados

Los resultados obtenidos pueden ser utilizados para:

* **Identificar oportunidades de mercado:**
    * Descubrir vinos de alta calidad a precios asequibles.
* **Mejorar la experiencia del usuario:**
    * Ofrecer recomendaciones personalizadas.
* **Entender las preferencias de los consumidores:**
    * Analizar el sentimiento en las reseñas.
 ------------------------------------------------------------------------------------------------------------------------------------------------------------------------        


## Etapas del Proyecto

### 1. Exploración y Limpieza de Datos (EDA & ETL)

* **Carga del Dataset**:
    * Utilización de la API de Kaggle para la descarga del conjunto de datos de vinos.
* **Análisis Exploratorio**:
    * Identificación de valores nulos, duplicados e inconsistencias en los datos.
* **Manejo de Valores Faltantes**:
    * Justificación y aplicación de una estrategia adecuada para el tratamiento de valores faltantes.
* **Visualización de Distribuciones**:
    * Generación de gráficos para comprender la distribución de variables clave como precio y puntuación.
* **Creación de Nuevas Variables**:
    * Segmentación de precios en rangos para facilitar el análisis.

### 2. Análisis de Precios y Factores de Calidad

* **Relación Precio-Puntuación**:
    * Análisis de la correlación entre el precio y la calidad (puntuación) de los vinos.
* **Identificación de la Mejor Relación Calidad-Precio**:
    * Determinación de regiones y variedades de uva que ofrecen la mejor relación calidad-precio.
* **Predicción de Precios**:
    * Aplicación de técnicas de regresión para predecir el precio de un vino en función de sus características.

### 3. Análisis de Sentimiento en Reseñas (NLP)

* **Limpieza de Datos de Texto**:
    * Eliminación de stopwords, aplicación de técnicas de stemming y lematización para preparar el texto.
* **Análisis de Frecuencia de Palabras**:
    * Identificación de las palabras más comunes en reseñas de vinos con puntuaciones altas y bajas.
* **Modelo de Análisis de Sentimiento**:
    * Construcción de un modelo para clasificar las reseñas como positivas o negativas.
* **Visualización de Resultados**:
    * Utilización de nubes de palabras para representar los términos más frecuentes en reseñas positivas y negativas.

### 4. Sistema de Recomendación de Vinos

* **Recomendación Basada en Contenido**:
    * Generación de recomendaciones basadas en características como variedad, país, etc.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------  
* **Recomendación Colaborativa**:
    * Implementación de un sistema de recomendación basado en la similitud entre las puntuaciones de los usuarios.

- **Pandas**: Para manipulación y análisis de datos.
- **NumPy**: Para operaciones numéricas.
- **Matplotlib y Seaborn**: Para visualización de datos.
- **Scikit-learn**: Para modelos de machine learning.
- **NLTK y SpaCy**: Para procesamiento de lenguaje natural (NLP).
- **TensorFlow/Keras**: Para el modelo de análisis de sentimiento.
- **Surprise**: Para el sistema de recomendación colaborativa.

[Documentación de Pandas](https://pandas.pydata.org/docs/)       
[Documentación de Scikit-learn](https://scikit-learn.org/stable/)   
[Documentación de NLTK](https://www.nltk.org/)    
[Documentación de TensorFlow/Keras](https://www.tensorflow.org/api_docs)        
[Documentación de Surprise](https://surprise.readthedocs.io/en/stable/)

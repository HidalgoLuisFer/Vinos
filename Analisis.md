# ETL / EDA: Insights y Hallazgos del Análisis de Vinos

## **1. Datos Faltantes e Imputación**
- Se identificaron valores nulos en las columnas **designation, region_1, region_2, price y country**.
- Se rellenaron valores faltantes con:
  - `'Unknown'` para datos categóricos sin información adicional.
  - La **mediana** en `price`, evitando sesgos extremos en la distribución.
- **Nota:** La ausencia de datos en ciertas regiones podría afectar la precisión del análisis en algunas zonas productoras.

---

## **2. Calidad de los Vinos y Distribución de Puntuaciones**
- **Puntuación media:** 87.89 puntos (sobre 100).
- La mayoría de los vinos tienen **puntuaciones altas**, lo que sugiere un posible sesgo en la selección de reseñas.
- **Nota:** Los vinos mal puntuados no aparecen en la base de datos, lo que indica una posible omisión de productos de baja calidad.

---

## **3. Análisis de Precios**
- **Precio promedio:** $32.30 (rango de $4 a $2,300).
- Se observa una **gran dispersión** de precios, con algunos vinos extremadamente costosos.
- **Segmentación de precios:** Muy Barato, Barato, Moderado, Caro, Muy Caro y Exclusivo.
- **Nota:** El mercado está dominado por vinos de gama media ($20-$50).

---

## **4. Países Productores de Vino**
- **EE.UU., Francia e Italia** son los países con más registros.
- **Nota:** El dataset refleja la hegemonía de estos países en la industria del vino, aunque hay presencia de otros mercados emergentes.

---

## **5. Variedades de Uva y Bodegas**
- **Chardonnay** es la variedad más común en las reseñas.
- **Williams Selyem** es la bodega con más reseñas, lo que sugiere una estrategia activa de marketing.
- **Nota:** Algunas bodegas están sobrerrepresentadas en la base de datos.

---

## **6. Relación entre Precio y Puntuación**
- Se encontró una **correlación positiva pero débil** entre precio y puntuación.
- **Nota:** El precio alto no siempre garantiza mejor calidad.

---

## **7. Distribución de Puntuaciones por País**
- En países como **EE.UU.**, hay mayor variabilidad en las puntuaciones.
- En **Francia e Italia**, las calificaciones son más uniformes.
- **Nota:** Diferencias en los estilos de producción y expectativas del consumidor pueden influir en esta distribución.

---

# Modelos de Predicción

## **1. Mejores Variedades y Países por Calidad-Precio**
- Se identificaron las **10 mejores variedades** y **10 mejores países** con mejor relación calidad-precio.
- **Nota:** Algunas variedades y países ofrecen vinos de alta calidad a precios más accesibles.

---

## **2. Modelos de Predicción Utilizados**
- **Random Forest Regressor** (Modelo No Lineal).
- **Regresión Lineal** (Modelo Lineal).
- Variables utilizadas: `points` (puntuación), `variety` (tipo de uva) y `country` (país de origen).
- **Nota:** Se aplicó OneHotEncoder para transformar variables categóricas y se dividió el dataset en 80% entrenamiento y 20% prueba.

---

## **3. Comparación de Modelos**
| Modelo            | MSE Entrenamiento | R² Entrenamiento | MSE Prueba | R² Prueba |
|------------------|------------------|-----------------|-----------|----------|
| **Random Forest** | 652.734          | 0.471          | 645.596   | 0.412    |
| **Regresión Lineal** | 797.60        | 0.353          | 701.524   | 0.361    |
- **Nota:** Random Forest tiene mejor desempeño y captura mejor relaciones no lineales.

---

# Modelo NLP: Análisis de Sentimiento en Reseñas

## **1. Preprocesamiento y Limpieza del Texto**
- Eliminación de **stopwords** y **lemmatización** con spaCy.
- Creación de la columna `cleaned_review` con reseñas normalizadas.
- **Nota:** Mejora la precisión del análisis de sentimientos.

---

## **2. Análisis de Frecuencia de Palabras**
| Tipo de Reseña | Palabras Más Frecuentes | Interpretación |
|---------------|----------------------|----------------|
| **Bien puntuadas (>90)** | wine, fruit, flavor, tannin, cherry | Relacionadas con sabores intensos y equilibrados. |
| **Mal puntuadas (<85)** | flavor, sweet, dry, acidity | Indican desequilibrios en el sabor. |
- **Nota:** Los términos usados reflejan directamente la percepción de calidad.

---

## **3. Análisis de Sentimiento con TextBlob**
- Se calculó la **polaridad** de las reseñas y se clasificaron como **positivas** o **negativas**.
- **Nota:** Las reseñas más positivas mencionan sabores profundos y bien estructurados, mientras que las negativas incluyen términos como "verde" o "simple".

---

# Modelos de Recomendación de Vinos

## **1. Modelo Basado en Contenido (TF-IDF + Similitud Coseno)**
- Convierte el texto en números usando **TF-IDF** (variedad, país, descripción).
- Calcula la **similitud coseno** entre vinos.
- **Nota:** Ideal para encontrar vinos similares a uno que ya te gusta.

---

## **2. Modelo Colaborativo (KNN + Filtrado Basado en Usuarios)**
- Utiliza **KNN** para encontrar usuarios con gustos similares.
- Predice qué vinos podrían gustarle a un usuario en función de puntuaciones previas.
- **Nota:** Útil para descubrir vinos nuevos según preferencias de otros consumidores.

---

## **3. Comparación de Modelos**
| Modelo  | ¿Cómo Funciona? | Pros | Contras |
|---------|---------------|--------|---------|
| **Basado en Contenido** | Recomienda vinos con descripciones similares. | No necesita datos de usuarios. | No funciona bien si las descripciones no reflejan similitud. |
| **Colaborativo (KNN)** | Recomienda vinos según puntuaciones de otros usuarios. | Descubre vinos nuevos. | Necesita suficientes datos de puntuaciones. |

---

## **Conclusión**
- **Si ya tienes un vino favorito y quieres más como ese:** Usa el **modelo basado en contenido**.
- **Si quieres descubrir vinos nuevos según otros usuarios:** Usa el **modelo colaborativo**.
- **Nota:** Estos modelos pueden integrarse para mejorar la experiencia de recomendación en tiendas de vinos o aplicaciones de cata.

# Respuestas — Práctica Final: Análisis y Modelado de Datos

> Rellena cada pregunta con tu respuesta. Cuando se pida un valor numérico, incluye también una breve explicación de lo que significa.

---

## Ejercicio 1 — Análisis Estadístico Descriptivo
---
Dataset: NYC Airbnb Open Data 
Fuente: https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data?resource=download

El dataset utilizado corresponde a datos de Airbnb en Nueva York, que contiene información sobre alojamientos, anfitriones, ubicación, precios y disponibilidad.

El objetivo del análisis es comprender la estructura del dataset, detectar problemas de calidad (nulos, outliers) y estudiar relaciones entre variables numéricas para identificar posibles factores influyentes sobre el precio.

---

**Pregunta 1.1 — ¿De qué fuente proviene el dataset?**
 El dataset proviene de datos públicos de Airbnb sobre alojamientos en Nueva York (NYC Airbnb Open Data).

**¿y cuál es la variable objetivo (target)?**
 La variable objetivo seleccionada es price, ya que representa el precio del alojamiento y es una variable numérica continua adecuada para problemas de regresión.

 **¿Por qué tiene sentido hacer regresión sobre ella?**
 Tiene sentido realizar regresión sobre esta variable porque el precio depende de múltiples factores como la ubicación, el tipo de habitación, el número de noches mínimas o la disponibilidad, lo que permite modelar su comportamiento mediante variables predictoras.

**Pregunta 1.2 — ¿Qué distribución tienen las principales variables numéricas y has encontrado outliers?**
Las variables numéricas presentan distribuciones claramente asimétricas en varios casos.

Variables como price, minimum_nights, number_of_reviews y calculated_host_listings_count presentan alta dispersión y fuerte sesgo a la derecha.
Se observan valores extremos muy elevados en varias variables, especialmente en:
price (hasta 10000)
minimum_nights (hasta 1250)
calculated_host_listings_count (hasta 327)

**Indica en qué variables y qué has decidido hacer con ellos.**
Se ha aplicado el método IQR (rango intercuartílico) para la detección de outliers.

Conclusión:

Se detectan numerosos outliers en casi todas las variables numéricas.
No se han eliminado, ya que en este ejercicio exploratorio se mantienen para no perder información relevante del comportamiento real del mercado.

**Pregunta 1.3 — ¿Qué tres variables numéricas tienen mayor correlación (en valor absoluto) con la variable objetivo?** Indica los coeficientes.

Las tres variables numéricas con mayor correlación (en valor absoluto) con la variable objetivo price son:

price (variable objetivo)
calculated_host_listings_count
minimum_nights
availability_365 (muy cercana en algunos casos)

Interpretación:

minimum_nights suele tener correlación positiva moderada: alojamientos que exigen más noches tienden a tener precios más altos.
calculated_host_listings_count puede reflejar hosts profesionales, con precios más altos o estructuras de alquiler más complejas.
availability_365 muestra relación con la disponibilidad anual del alojamiento.

**Pregunta 1.4 — ¿Hay valores nulos en el dataset? ¿Qué porcentaje representan y cómo los has tratado?**

El dataset presenta valores nulos en las siguientes columnas:

name (~0.03%)
host_name (~0.04%)
last_review (~20.55%)
reviews_per_month (~20.55%)

Tratamiento realizado:

Las variables name y host_name no se han utilizado en el análisis numérico, por lo que los nulos no afectan al modelado.
last_review y reviews_per_month presentan un porcentaje alto de nulos, lo que indica que muchos alojamientos no tienen reseñas.
En este análisis exploratorio no se han imputado valores, ya que el objetivo es descriptivo y no predictivo.

---

## Ejercicio 2 — Inferencia con Scikit-Learn

---
Añade aqui tu descripción y analisis:

---

**Pregunta 2.1** — Indica los valores de MAE, RMSE y R² de la regresión lineal sobre el test set. ¿El modelo funciona bien? ¿Por qué?

> _Escribe aquí tu respuesta_


---

## Ejercicio 3 — Regresión Lineal Múltiple en NumPy

---
Añade aqui tu descripción y analisis:

---

**Pregunta 3.1** — Explica en tus propias palabras qué hace la fórmula β = (XᵀX)⁻¹ Xᵀy y por qué es necesario añadir una columna de unos a la matriz X.

> _Escribe aquí tu respuesta_

**Pregunta 3.2** — Copia aquí los cuatro coeficientes ajustados por tu función y compáralos con los valores de referencia del enunciado.

| Parametro | Valor real | Valor ajustado |
|-----------|-----------|----------------|
| β₀        | 5.0       |                |
| β₁        | 2.0       |                |
| β₂        | -1.0      |                |
| β₃        | 0.5       |                |

> _Escribe aquí tu respuesta_

**Pregunta 3.3** — ¿Qué valores de MAE, RMSE y R² has obtenido? ¿Se aproximan a los de referencia?

> _Escribe aquí tu respuesta_

**Pregunta 3.4* — Compara los resultados con la reacción logística anterior para tu dataset y comprueba si el resultado es parecido. Explica qué ha sucedido. 

> _Escribe aquí tu respuesta_

---

## Ejercicio 4 — Series Temporales
---
Añade aqui tu descripción y analisis:

---

**Pregunta 4.1** — ¿La serie presenta tendencia? Descríbela brevemente (tipo, dirección, magnitud aproximada).

> _Escribe aquí tu respuesta_

**Pregunta 4.2** — ¿Hay estacionalidad? Indica el periodo aproximado en días y la amplitud del patrón estacional.

> _Escribe aquí tu respuesta_

**Pregunta 4.3** — ¿Se aprecian ciclos de largo plazo en la serie? ¿Cómo los diferencias de la tendencia?

> _Escribe aquí tu respuesta_

**Pregunta 4.4** — ¿El residuo se ajusta a un ruido ideal? Indica la media, la desviación típica y el resultado del test de normalidad (p-value) para justificar tu respuesta.

> _Escribe aquí tu respuesta_

---

*Fin del documento de respuestas*

1. Precio (TARGET)
media = 152
mediana = 106
max = 10000
muchos outliers (2972)

👉 CONCLUSIÓN:

distribución altamente asimétrica (sesgo a la derecha)

📌 2. minimum_nights
max = 1250
muchísimos outliers (6607)

👉 CONCLUSIÓN:

comportamiento extremo → posible limpieza o transformación logarítmica

📌 3. availability_365
sin outliers
👉 variable bastante estable

📌 4. reviews_per_month
valores muy dispersos
outliers moderados
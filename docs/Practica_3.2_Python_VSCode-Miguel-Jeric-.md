# Práctica 3.2: Primeros pasos con Python y Visual Studio Code (INAEM)

## 📋 Resumen
Este documento describe una práctica de Python centrada en la manipulación y análisis de datos. Incluye la gestión de un DataFrame de clientes con `pandas`, el entrenamiento de un modelo de regresión lineal para predecir precios de viviendas con `scikit-learn` y la generación de una visualización con `matplotlib`, todo ello ejecutado en Visual Studio Code.

## 🔑 Puntos clave
- **Manipulación de DataFrames:** Creación, adición, modificación y filtrado de datos de clientes usando `pandas`.
- **Cálculo de estadísticos descriptivos:** Obtención de la edad y compra media de clientes.
- **Modelo de Regresión Lineal:** Entrenamiento y uso de `scikit-learn` para predecir precios de viviendas.
- **Visualización de Datos:** Generación de un gráfico de barras con `matplotlib` para las compras por cliente.
- **Entorno de desarrollo:** La práctica se desarrolló y verificó en Visual Studio Code.

## 📝 Detalle

Esta práctica, realizada por Miguel Jericó como parte de su formación en "Análisis de Datos e IA" en el INAEM, aborda conceptos fundamentales de análisis de datos y machine learning en Python.

### Bloque 1: Manipulación de Datos de Clientes con `pandas`

Se inicia con un DataFrame de clientes y se realizan diversas operaciones para gestionar y analizar sus datos.

#### 1. Añadir un quinto cliente al DataFrame
Se crea un DataFrame inicial con cuatro clientes (Ana, Luis, Pedro, Marta) y sus respectivas edades y volúmenes de compra. Posteriormente, se añade un nuevo cliente, Elena, al DataFrame existente utilizando `pd.concat()`.

```python
import pandas as pd

datos = pd.DataFrame({
    "Nombre": ["Ana", "Luis", "Pedro", "Marta"],
    "Edad": [23, 35, 41, 29],
    "Compras": [120, 450, 380, 210]
})

nuevo_cliente = pd.DataFrame({"Nombre": ["Elena"], "Edad": [45], "Compras": [500]})
datos = pd.concat([datos, nuevo_cliente], ignore_index=True)
```

#### 2. Modificar las compras de Marta
Se actualiza el registro de compras del cliente "Marta" de 210 a 600, utilizando el acceso por etiqueta `.loc` para una modificación selectiva.

```python
datos.loc[datos["Nombre"] == "Marta", "Compras"] = 600
```

#### 3. Calcular la edad y la compra media
Se calculan la edad media de todos los clientes y la compra media total, aplicando el método `.mean()` directamente sobre las columnas correspondientes del DataFrame.

```python
# Edad media
edad_media = datos["Edad"].mean()

# Compra media
compra_media = datos["Compras"].mean()
```

#### 4. Filtrar clientes menores de 30 años
Se muestran únicamente los clientes cuya edad es estrictamente inferior a 30 años, empleando indexación booleana para realizar el filtrado.

```python
print(" = = - Ejercicio 4: Clientes menores de 30 años = = -")
print(datos[datos["Edad"] < 30])
print("\n")
```

### Bloque 2: Análisis Predictivo de Viviendas con `scikit-learn` y Visualización con `matplotlib`

Esta sección se enfoca en la implementación de un modelo de Machine Learning para la predicción de precios y la generación de un gráfico.

#### 5. Añadir una nueva vivienda y reentrenar el modelo
Se inicializa un DataFrame `datos_ml` con un conjunto de datos de viviendas que incluye metros cuadrados, número de habitaciones y precio. Se añade una novena vivienda (180 m², 5 habitaciones, 480.000€) al conjunto de entrenamiento y, posteriormente, se entrena un modelo de `LinearRegression` de `scikit-learn` con los datos actualizados.

```python
from sklearn.linear_model import LinearRegression

datos_ml = pd.DataFrame({
    "metros": [50, 60, 70, 80, 90, 100, 120, 150],
    "habitaciones": [1, 2, 2, 3, 3, 3, 4, 5],
    "precio": [120000, 150000, 180000, 210000, 240000, 270000, 320000, 400000]
})

nueva_vivienda_entrenamiento = pd.DataFrame({
    "metros": [180],
    "habitaciones": [5],
    "precio": [480000]
})

datos_ml = pd.concat([datos_ml, nueva_vivienda_entrenamiento], ignore_index=True)

X = datos_ml[["metros", "habitaciones"]]
y = datos_ml["precio"]

modelo = LinearRegression()
modelo.fit(X, y)
```

#### 6. Realizar una predicción y visualizar resultados
Se utiliza el modelo de regresión lineal entrenado para predecir el precio de una vivienda de 110 m² y 4 habitaciones, mostrando el resultado estimado por consola. Además, se incluye la generación de un gráfico de barras con `matplotlib.pyplot` para visualizar las "Compras por cliente" del primer bloque de la práctica.

```python
import matplotlib.pyplot as plt

vivienda_a_predecir = pd.DataFrame({
    "metros": [110],
    "habitaciones": [4]
})

prediccion = modelo.predict(vivienda_a_predecir)

print(" = = - Ejercicio 6: Predicción ML = = -")
print(f"Precio estimado (110m², 4 habs): "
      f"{str(round(prediccion[0], 2)).replace('.', ',')} €")

# Gráfico de barras: compras por cliente
plt.bar(datos["Nombre"], datos["Compras"])
plt.title("Compras por cliente")
plt.xlabel # Título del eje X (truncado en el documento original)
```

## ✅ Conclusiones / siguientes pasos
Esta práctica demuestra habilidades fundamentales en la manipulación de datos con `pandas`, el modelado predictivo con `scikit-learn` y la visualización básica con `matplotlib` en un entorno de desarrollo como Visual Studio Code. Como siguientes pasos, se podría:
- Ampliar el análisis de datos exploratorio (EDA) para obtener más insights.
- Evaluar el rendimiento del modelo de regresión lineal con métricas como el R² o el Error Cuadrático Medio (RMSE).
- Explorar otros tipos de modelos de machine learning para la predicción de precios.
- Desarrollar visualizaciones más complejas y personalizadas para presentar los resultados.
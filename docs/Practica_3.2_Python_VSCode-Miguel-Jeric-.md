# Práctica 3.2: Primeros pasos con Python y Visual Studio Code para Análisis de Datos

## 📋 Resumen
Este documento detalla la "Práctica 3.2: Primeros pasos con Python y Visual Studio Code", una actividad realizada por Miguel Jericó en el marco del programa INAEM Análisis de Datos e IA. La práctica abarca la manipulación de datos con la librería `pandas`, el entrenamiento de un modelo de regresión lineal utilizando `scikit-learn` y la generación de visualizaciones con `matplotlib`. Todo el proceso se ejecuta y verifica desde el entorno de desarrollo integrado Visual Studio Code, con el objetivo de introducir al alumno en herramientas fundamentales para el análisis de datos en Python.

## 🔑 Puntos clave
-   **Manipulación de DataFrames (`pandas`):** Creación, adición de filas, modificación de valores, cálculo de estadísticos descriptivos (medias) y filtrado de datos.
-   **Modelado de Regresión Lineal (`scikit-learn`):** Preparación de datos, entrenamiento de un modelo para predicción de precios de viviendas y realización de nuevas predicciones.
-   **Visualización de Datos (`matplotlib`):** Generación de gráficos de barras para representar datos.
-   **Entorno de Desarrollo:** Uso de Visual Studio Code como herramienta principal para ejecutar y gestionar el código Python de análisis de datos.
-   **Aplicación Práctica:** Ejercicios que simulan escenarios reales de gestión de clientes y análisis de mercado inmobiliario.

## 📝 Detalle

La práctica se divide en dos bloques principales: manipulación de un DataFrame de clientes y un ejercicio de regresión lineal para predicción de precios de viviendas, culminando con una visualización.

### Bloque 1: Manipulación de DataFrame de Clientes con Pandas

Este bloque se enfoca en las operaciones básicas de un DataFrame de `pandas` utilizando datos de clientes.

#### 01 Añadir un quinto cliente al DataFrame

Se crea un DataFrame inicial con cuatro clientes y se añade un quinto cliente (`Elena`) utilizando la función `pd.concat` para combinar DataFrames.

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

#### 02 Modificar las compras de Marta

Se actualiza el valor del campo `Compras` para el cliente "Marta" a 600, utilizando el acceso condicional `.loc`.

```python
datos.loc[datos["Nombre"] == "Marta", "Compras"] = 600
```

#### 03 Calcular la edad y la compra media

Se calcula la edad media de todos los clientes y la compra media utilizando el método `.mean()` en las columnas correspondientes.

```python
# Edad media
edad_media = datos["Edad"].mean()

# Compra media
compra_media = datos["Compras"].mean()
```

#### 04 Filtrar clientes menores de 30 años

Se muestran únicamente los clientes cuya edad es estrictamente inferior a 30 años mediante indexación booleana.

```python
print("= = - Ejercicio 4: Clientes menores de 30 años = = -")
print(datos[datos["Edad"] < 30])
print("\n")
```

### Bloque 2: Modelo de Regresión Lineal con Scikit-learn y Visualización

Este bloque aborda el entrenamiento de un modelo de machine learning y la creación de una visualización.

#### 05 Añadir una nueva vivienda y reentrenar el modelo

Se crea un DataFrame de entrenamiento para un modelo de regresión lineal con datos de viviendas (metros, habitaciones, precio). Posteriormente, se añade una nueva vivienda y se reentrena el modelo `LinearRegression` de `scikit-learn`.

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

#### 06 Realizar una predicción para una vivienda de 110 m² y 4 habitaciones

Utilizando el modelo entrenado en el paso anterior, se realiza una predicción del precio para una vivienda con características específicas (110 m² y 4 habitaciones) y se muestra el resultado formateado por consola.

```python
vivienda_a_predecir = pd.DataFrame({
    "metros": [110],
    "habitaciones": [4]
})

prediccion = modelo.predict(vivienda_a_predecir)

print("= = - Ejercicio 6: Predicción ML = = -")
print(f"Precio estimado (110m², 4 habs): "
      f"{str(round(prediccion[0], 2)).replace('.', ',')} €")
print("\n")
```

### Visualización de Datos con Matplotlib

Para finalizar la práctica, se genera un gráfico de barras que muestra las compras realizadas por cada cliente, utilizando la librería `matplotlib`.

```python
import matplotlib.pyplot as plt

# Gráfico de barras: compras por cliente
plt.bar(datos["Nombre"], datos["Compras"])
plt.title("Compras por cliente")
plt.xlabel("Cliente") # Implícito por el contexto, aunque truncado en el PDF
plt.ylabel("Compras (€)") # Implícito por el contexto
plt.show() # Para mostrar el gráfico
```

## ✅ Conclusiones / siguientes pasos
Esta práctica demuestra la aplicación fundamental de las librerías `pandas`, `scikit-learn` y `matplotlib` para tareas comunes en análisis de datos con Python, todo ello en el entorno de Visual Studio Code. Se ha logrado manipular datos estructurados, entrenar un modelo de machine learning y visualizar información.

Este documento puede ser un recurso valioso para la creación de un nuevo repositorio, como el que el usuario ha mencionado (`migueljerico/Ejercicio_R_VSCode`), sirviendo como referencia para futuras actividades relacionadas con el análisis de datos y la programación en Python.
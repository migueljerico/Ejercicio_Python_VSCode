# Práctica 3.2: Primeros Pasos con Python y Visual Studio Code para Análisis de Datos

## 📋 Resumen
Esta documentación describe la Práctica 3.2 realizada por Miguel Jericó, que cubre la manipulación de DataFrames con `pandas`, el entrenamiento de un modelo de regresión lineal con `scikit-learn` para la predicción de precios de viviendas y la generación de una visualización con `matplotlib`. Todos los ejercicios se han ejecutado y verificado desde Visual Studio Code como parte de una formación en Análisis de Datos e IA.

## 🔑 Puntos clave
- **Manipulación de DataFrames con `pandas`**: Operaciones de añadir, modificar y filtrar datos de clientes.
- **Cálculo de estadísticos descriptivos**: Obtención de medias de columnas en un DataFrame.
- **Modelado predictivo con `scikit-learn`**: Entrenamiento y uso de un modelo de regresión lineal para la predicción de precios de viviendas.
- **Visualización de datos con `matplotlib`**: Creación de gráficos de barras para representar información.
- **Entorno de desarrollo**: Toda la práctica se realiza en Python y Visual Studio Code.

## 📝 Detalle

### Contexto de la Práctica
La Práctica 3.2, desarrollada por Miguel Jericó en el marco de la formación "INAEM Análisis de Datos e IA", se centra en la aplicación de herramientas clave de Python para el análisis de datos dentro del entorno de Visual Studio Code. Abarca desde la gestión básica de datos hasta el aprendizaje automático y la visualización.

### 1. Manipulación de un DataFrame de Clientes con Pandas

Se crea y manipula un DataFrame inicial de clientes utilizando la librería `pandas`.

#### 1.1. Añadir un Quinto Cliente
Se añade un nuevo cliente, "Elena", al DataFrame existente utilizando la función `pd.concat`.

```python
datos = pd.DataFrame({
    "Nombre": ["Ana", "Luis", "Pedro", "Marta"],
    "Edad": [23, 35, 41, 29],
    "Compras": [120, 450, 380, 210]
})

nuevo_cliente = pd.DataFrame({"Nombre": ["Elena"], "Edad": [45], "Compras": [500]})
datos = pd.concat([datos, nuevo_cliente], ignore_index=True)
```

#### 1.2. Modificar las Compras de un Cliente
Se actualiza el valor del campo "Compras" para el cliente "Marta" utilizando el acceso por etiqueta `.loc`.

```python
datos.loc[datos["Nombre"] == "Marta", "Compras"] = 600
```

#### 1.3. Calcular Edad y Compra Media
Se calculan la edad media de los clientes y la compra media utilizando el método `.mean()` sobre las columnas correspondientes.

```python
# Edad media
edad_media = datos["Edad"].mean()

# Compra media
compra_media = datos["Compras"].mean()
```

#### 1.4. Filtrar Clientes Menores de 30 Años
Se muestran únicamente los clientes cuya edad es estrictamente inferior a 30 años mediante indexación booleana.

```python
print(" = = - Ejercicio 4: Clientes menores de 30 años   = = -")
print(datos[datos["Edad"] < 30])
print("\n")
```

### 2. Entrenamiento y Predicción con Modelo de Regresión Lineal

Se prepara un conjunto de datos de viviendas para el entrenamiento de un modelo de regresión lineal y se utiliza para realizar predicciones.

#### 2.1. Añadir Nueva Vivienda y Reentrenar el Modelo
Se incorpora una novena vivienda al DataFrame de entrenamiento y se reentrena un modelo de regresión lineal utilizando `scikit-learn`.

```python
import pandas as pd
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

#### 2.2. Realizar una Predicción
Se utiliza el modelo entrenado para estimar el precio de una vivienda con 110 m² y 4 habitaciones, mostrando el resultado por consola.

```python
vivienda_a_predecir = pd.DataFrame({
    "metros": [110],
    "habitaciones": [4]
})

prediccion = modelo.predict(vivienda_a_predecir)

print(" = = - Ejercicio 6: Predicción ML   = = -")
print(f"Precio estimado (110m², 4 habs): "
      f"{str(round(prediccion[0], 2)).replace('.', ',')} €")
```

### 3. Visualización de Datos con Matplotlib

Se genera una visualización básica de las compras por cliente utilizando la librería `matplotlib`.

```python
import matplotlib.pyplot as plt

plt.bar(datos["Nombre"], datos["Compras"])
plt.title("Compras por cliente")
plt.xlabe
```

## ✅ Conclusiones / siguientes pasos
Esta práctica demuestra la capacidad de realizar tareas fundamentales de análisis de datos en Python utilizando librerías como `pandas`, `scikit-learn` y `matplotlib` dentro del entorno de Visual Studio Code. Cubre desde la manipulación básica de DataFrames hasta el desarrollo de un modelo predictivo simple y su visualización, sirviendo como una base sólida para proyectos de análisis de datos e inteligencia artificial.

Esta documentación ha sido generada para acompañar el registro de la actividad de clase, facilitando su comprensión y futura referencia.
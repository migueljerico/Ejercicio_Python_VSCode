# 📊 Práctica 3.2: Análisis de Datos y ML con Python en VS Code

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white) ![Scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=matplotlib&logoColor=white) ![Estado](https://img.shields.io/badge/Estado-En%20desarrollo-blue.svg?style=for-the-badge) ![Licencia](https://img.shields.io/badge/Licencia-MIT-green.svg?style=for-the-badge)

*Una práctica formativa que explora la manipulación de datos con `pandas`, el entrenamiento de modelos de regresión lineal con `scikit-learn` y la visualización con `matplotlib` en Visual Studio Code.*


## 🔗 Acceso / Demo
Este proyecto es una práctica de código local en Python. Para ejecutarlo, sigue las instrucciones detalladas en las secciones de Instalación y Uso.

## 📋 Descripción
Este repositorio contiene el código de la Práctica 3.2, una iniciativa formativa del programa "Análisis de Datos e IA" del INAEM. El objetivo principal es familiarizar a los estudiantes con las herramientas fundamentales del ecosistema Python para el análisis de datos y el machine learning.

La práctica se divide en dos bloques principales: primero, la manipulación de DataFrames de clientes utilizando la librería `pandas` para tareas como adición, modificación y filtrado de datos, junto con el cálculo de estadísticas descriptivas. Segundo, se aborda la implementación de un modelo de regresión lineal con `scikit-learn` para predecir precios de viviendas y la generación de visualizaciones de datos con `matplotlib`.

Todo el desarrollo se ha realizado y verificado dentro del entorno de Visual Studio Code, sirviendo como una guía práctica para el manejo de proyectos de análisis de datos desde este popular IDE.

## ✨ Funcionalidades
| Funcionalidad                       | Descripción                                                                               |
| :---------------------------------- | :---------------------------------------------------------------------------------------- |
| Manipulación de DataFrames          | Crear, añadir, modificar y filtrar datos de clientes usando `pandas`.                     |
| Cálculo de Estadísticos Descriptivos | Obtener la edad media y el volumen de compra medio de los clientes.                       |
| Modelado de Regresión Lineal        | Entrenar y utilizar un modelo de `scikit-learn` para predecir precios de viviendas.       |
| Visualización de Datos              | Generar gráficos de barras con `matplotlib` para representar las compras por cliente.     |
| Gestión de Datos Inmobiliarios      | Añadir y reentrenar modelos predictivos con nuevos datos de viviendas para mejorar la precisión. |

## ⚙️ Instalación
Para poner en marcha el proyecto, sigue los siguientes pasos:

1.  **Clonar el repositorio:**
    ```bash
    git clone https://github.com/migueljerico/Ejercicio_Python_VSCode.git
    cd Ejercicio_Python_VSCode
    ```

2.  **Crear y activar un entorno virtual (recomendado):**
    ```bash
    python -m venv .venv
    # En Windows:
    .venv\Scripts\activate
    # En macOS/Linux:
    source .venv/bin/activate
    ```

3.  **Instalar las dependencias:**
    ```bash
    pip install pandas scikit-learn matplotlib
    ```

## 🚀 Uso
El código de la práctica se encuentra en el archivo `practice_script.py`. Una vez instalado el entorno y las dependencias, puedes ejecutar los ejemplos directamente.

Para ejecutar el script completo que incluye todas las operaciones descritas:
```bash
python practice_script.py
```

A continuación, se presentan los bloques de código y su funcionalidad:

### Bloque 1: Manipulación de Datos de Clientes con `pandas`

```python
import pandas as pd

print("=== Bloque 1: Manipulación de Datos de Clientes ===")

datos = pd.DataFrame({
    "Nombre": ["Ana", "Luis", "Pedro", "Marta"],
    "Edad": [23, 35, 41, 29],
    "Compras": [120, 450, 380, 210]
})

print("DataFrame inicial de clientes:")
print(datos)
print("\n")

# 1. Añadir un quinto cliente al DataFrame
nuevo_cliente = pd.DataFrame({"Nombre": ["Elena"], "Edad": [45], "Compras": [500]})
datos = pd.concat([datos, nuevo_cliente], ignore_index=True)
print("1. DataFrame con Elena añadida:")
print(datos)
print("\n")

# 2. Modificar las compras de Marta
datos.loc[datos["Nombre"] == "Marta", "Compras"] = 600
print("2. Compras de Marta modificadas a 600:")
print(datos)
print("\n")

# 3. Calcular la edad y la compra media
edad_media = datos["Edad"].mean()
compra_media = datos["Compras"].mean()
print(f"3. Edad media de los clientes: {edad_media:.2f} años")
print(f"   Compra media de los clientes: {compra_media:.2f} €")
print("\n")

# 4. Filtrar clientes menores de 30 años
print("4. Clientes menores de 30 años:")
print(datos[datos["Edad"] < 30])
print("\n")
```

### Bloque 2: Análisis Predictivo de Viviendas con `scikit-learn` y Visualización con `matplotlib`

```python
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt

print("=== Bloque 2: Análisis Predictivo y Visualización ===")

datos_ml = pd.DataFrame({
    "metros": [50, 60, 70, 80, 90, 100, 120, 150],
    "habitaciones": [1, 2, 2, 3, 3, 3, 4, 5],
    "precio": [120000, 150000, 180000, 210000, 240000, 270000, 320000, 400000]
})

# 5. Añadir una nueva vivienda y reentrenar el modelo
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

print("5. Modelo de Regresión Lineal reentrenado.")
print(f"   Coeficientes del modelo: {modelo.coef_}")
print(f"   Intercepción del modelo: {modelo.intercept_:.2f}\n")

# 6. Predecir el precio de una vivienda de 110 m2 y 3 habitaciones
nueva_vivienda_prediccion = pd.DataFrame({
    "metros": [110],
    "habitaciones": [3]
})
precio_predicho = modelo.predict(nueva_vivienda_prediccion)[0]

print(f"6. Precio predicho para una vivienda de 110 m² y 3 habitaciones: {precio_predicho:.2f} €\n")

# 7. Visualizar las compras por cliente
# Reutilizamos el DataFrame 'datos' del bloque 1 para la visualización
plt.figure(figsize=(10, 6))
plt.bar(datos["Nombre"], datos["Compras"], color='skyblue')
plt.xlabel("Cliente")
plt.ylabel("Volumen de Compras (€)")
plt.title("7. Volumen de Compras por Cliente")
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show() # Mostrar el gráfico
```

## 📁 Estructura del proyecto
```
.
├── .venv/                                       # Entorno virtual de Python (Ignorado por Git)
├── docs/
│   └── Practica_3.2_Python_VSCode-Miguel-Jeric-.md # Documento original con la descripción de la práctica
├── practice_script.py                           # Script principal con el código de la práctica
└── README.md                                    # Documentación del proyecto (este archivo)
```

## 🛠️ Tecnologías
| Herramienta           | Versión/Detalle | Uso en el proyecto                                            |
| :-------------------- | :-------------- | :------------------------------------------------------------ |
| `Python`              | 3.x             | Lenguaje de programación principal para el desarrollo de la práctica. |
| `pandas`              | Última estable  | Manipulación y análisis de datos tabulares, gestión de DataFrames. |
| `scikit-learn`        | Última estable  | Implementación de algoritmos de Machine Learning, específicamente Regresión Lineal. |
| `matplotlib`          | Última estable  | Creación de gráficos y visualizaciones de datos.              |
| `Visual Studio Code`  | N/A             | Entorno de desarrollo integrado (IDE) utilizado para la codificación y depuración. |

## 📚 Contexto formativo o motivación del proyecto
Este proyecto forma parte de la Práctica 3.2, desarrollada por Miguel Jericó dentro del curso de "Análisis de Datos e IA" impartido por el INAEM. Su propósito es consolidar los conocimientos adquiridos en la gestión de datos, el modelado predictivo básico y la visualización de resultados mediante las herramientas estándar del ecosistema Python, utilizando Visual Studio Code como entorno de desarrollo.

<p align="center">Desarrollado por @migueljerico · 2026</p>
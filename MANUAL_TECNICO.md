## 🏗️ Arquitectura General

La práctica se concibe como un flujo secuencial de procesamiento de datos y modelado, ejecutado dentro de un único script Python. No sigue una arquitectura de capas tradicional de una aplicación web, sino más bien un pipeline de análisis de datos.

```
Flujo de la Práctica de Análisis de Datos y ML

+--------------------------+
|  Inicialización de Datos |
|  (DataFrames de Pandas)  |
+-----------+--------------+
            |
            v
+-----------+--------------+
|  Bloque 1: Manipulación  |
|  de Datos de Clientes    |
|  - Creación de DF        |
|  - Añadir/Modificar filas|
|  - Filtrado de datos     |
|  - Cálculos Estadísticos |
|  (Uso: pandas)           |
+-----------+--------------+
            |
            v
+-----------+--------------+
|  Bloque 2: Análisis      |
|  Predictivo y            |
|  Visualización           |
|  - Inicialización de DF  |
|  - Entrenamiento Modelo  |
|  - Predicción de valores |
|  - Generación de Gráficos|
|  (Uso: scikit-learn,     |
|        matplotlib)       |
+-----------+--------------+
            |
            v
+-----------+--------------+
|  Salida de Resultados    |
|  (Consola y Ventana      |
|   de Gráfico Matplotlib) |
+--------------------------+
```

## 🧩 Descripción de Módulos y Componentes Principales

El proyecto se organiza en un script principal que encapsula toda la lógica de la práctica. Los "módulos" son, en este contexto, bloques lógicos dentro de este script que utilizan librerías específicas de Python.

### `practice_script.py`

Este archivo es el corazón del proyecto y contiene la implementación completa de la práctica.

*   **Responsabilidad:** Ejecutar las operaciones de manipulación de datos, modelado predictivo y visualización según lo especificado en la práctica.

*   **Bloque 1: Manipulación de Datos de Clientes**
    *   **Propósito:** Demostrar operaciones fundamentales de gestión y análisis de datos tabulares utilizando la librería `pandas`.
    *   **Funciones/Métodos Clave Utilizados:**
        *   `pd.DataFrame()`: Para la creación de DataFrames iniciales.
        *   `pd.concat()`: Para la adición de nuevas filas (clientes) al DataFrame existente.
        *   `.loc[]`: Para la selección basada en etiquetas y modificación de valores específicos dentro del DataFrame (e.g., actualizar compras de un cliente).
        *   `.mean()`: Para el cálculo de la media de columnas numéricas (edad media, compra media).
        *   Indexación booleana (`datos[datos["Edad"] < 30]`): Para el filtrado de filas que cumplen una condición específica.

*   **Bloque 2: Análisis Predictivo de Viviendas y Visualización**
    *   **Propósito:** Implementar un modelo de Machine Learning (Regresión Lineal) para predicción y generar una visualización gráfica de datos.
    *   **Funciones/Métodos Clave Utilizados:**
        *   `sklearn.linear_model.LinearRegression()`: Clase para crear y gestionar el modelo de regresión lineal.
        *   `modelo.fit(X, y)`: Método para entrenar el modelo, donde `X` son las características de entrada y `y` es la variable objetivo.
        *   `modelo.predict(X_new)`: Método para obtener predicciones sobre nuevos datos de entrada (`X_new`).
        *   `matplotlib.pyplot.figure()`, `.bar()`, `.xlabel()`, `.ylabel()`, `.title()`, `.show()`: Conjunto de funciones para la creación, personalización y visualización de gráficos de barras.

## 🔌 APIs y Endpoints Documentados

Este proyecto es un script de ejecución local para análisis de datos y Machine Learning. No expone ninguna API RESTful ni endpoints HTTP, por lo que esta sección no aplica.

## ⚙️ Variables de Entorno

Este proyecto no utiliza variables de entorno para su configuración o ejecución. Todos los parámetros se definen directamente en el código del script.

## 🚀 Guía de Despliegue

El despliegue de este proyecto consiste en su ejecución local en un entorno Python.

### Requisitos Previos
*   **Python 3.x:** Asegúrate de tener una versión reciente de Python instalada en tu sistema.
*   **`pip`:** El gestor de paquetes de Python, que normalmente viene incluido con la instalación de Python.

### Pasos para la Ejecución Local

1.  **Clonar el Repositorio:**
    Abre tu terminal o línea de comandos y clona el repositorio:
    ```bash
    git clone https://github.com/migueljerico/Ejercicio_Python_VSCode.git
    cd Ejercicio_Python_VSCode
    ```

2.  **Preparar el Entorno Virtual (Opcional pero Recomendado):**
    Es una buena práctica crear un entorno virtual para aislar las dependencias del proyecto.
    ```bash
    python -m venv .venv
    # Activar el entorno virtual:
    # En Windows:
    .venv\Scripts\activate
    # En macOS/Linux:
    source .venv/bin/activate
    ```

3.  **Instalar Dependencias:**
    Con el entorno virtual activado, instala las librerías necesarias:
    ```bash
    pip install pandas scikit-learn matplotlib
    ```

4.  **Ejecutar el Script de la Práctica:**
    Una vez instaladas las dependencias, puedes ejecutar el script principal:
    ```bash
    python practice_script.py
    ```
    *   Los resultados de la manipulación de datos y las predicciones se mostrarán en la consola.
    *   El gráfico de barras de `matplotlib` se abrirá en una ventana emergente separada.

## 🚧 Limitaciones Conocidas y Posibles Mejoras Futuras

### Limitaciones Conocidas
*   **Escalabilidad:** El código está diseñado para fines educativos y para conjuntos de datos pequeños. No está optimizado para procesar grandes volúmenes de datos o para entornos de producción con altos requisitos de rendimiento.
*   **Modularidad y Estructura:** Toda la lógica de la práctica reside en un único script. Esto puede dificultar el mantenimiento y la escalabilidad en proyectos más complejos, donde sería preferible una separación de responsabilidades en diferentes módulos o archivos.
*   **Robustez y Manejo de Errores:** El script no incluye un manejo robusto de errores o validación de datos de entrada, asumiendo que los datos están limpios y en el formato esperado.
*   **Persistencia:** Los DataFrames y el modelo entrenado no se guardan ni se cargan de forma persistente, lo que significa que el estado se pierde entre ejecuciones.
*   **Interfaz de Usuario:** La interacción se limita a la consola y a una ventana gráfica básica, sin una interfaz de usuario más elaborada.

### Posibles Mejoras Futuras
*   **Modularización del Código:** Refactorizar el `practice_script.py` en funciones y módulos más pequeños y especializados (e.g., `data_preprocessing.py`, `model_training.py`, `visualization.py`) para mejorar la legibilidad y mantenibilidad.
*   **Configuración Externa:** Implementar un archivo de configuración (e.g., `.ini`, `YAML`, `.env`) para parámetros como rutas de archivos de datos, hiperparámetros del modelo o nombres de columnas, facilitando la adaptabilidad del script.
*   **Pruebas Unitarias:** Añadir un conjunto de pruebas unitarias para las funciones de manipulación de datos, entrenamiento del modelo y generación de gráficos, asegurando la fiabilidad del código.
*   **Serialización de Modelos:** Integrar la capacidad de guardar y cargar el modelo de `scikit-learn` utilizando `joblib` o `pickle`, permitiendo su reutilización sin necesidad de reentrenamiento.
*   **Gestión de Datos:** Expandir la práctica para leer datos de archivos externos (CSV, Excel) y explorar técnicas de preprocesamiento de datos más avanzadas (manejo de valores nulos, escalado, codificación categórica).
*   **Dashboard Interactivo:** Desarrollar una interfaz de usuario web sencilla utilizando librerías como `Streamlit` o `Dash` para permitir una interacción más dinámica con el modelo y los resultados.
*   **Integración Continua/Despliegue Continuo (CI/CD):** Establecer un pipeline básico de CI/CD para automatizar las pruebas y el despliegue del script, mejorando la calidad del software.
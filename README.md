# Autoencoders Variacionales (VAE) para Generación y Modificación de Rasgos Faciales

## Objetivo

El objetivo de este repositorio es utilizar la técnica de Autoencoder Variacional (VAE) para aprender una representación latente de imágenes de rostros humanos, permitiendo así modificar y generar únicamente los rasgos predominantes de la cara. El modelo es capaz de reconstruir imágenes y generar nuevas caras realistas a partir del espacio latente aprendido.

## Descripción del Proyecto

El flujo de trabajo está documentado en el notebook `autoencoders.ipynb` y se compone de las siguientes etapas:

### 1. Importación de Librerías y Carga de Datos
- Se utilizan librerías como TensorFlow, Keras, NumPy, Matplotlib y PIL.
- El dataset utilizado es CelebA, que contiene alrededor de 200,000 imágenes de rostros humanos de famosos.
- Las imágenes se cargan, redimensionan a 64x64 píxeles y se normalizan.

### 2. Visualización de Datos
- Se muestran ejemplos de imágenes del dataset para verificar la correcta carga y preprocesamiento.

### 3. Construcción del Modelo VAE
- **Encoder:** Red convolucional profunda que comprime la imagen en un vector latente (media y varianza logarítmica).
- **Decoder:** Red convolucional transpuesta que reconstruye la imagen a partir del vector latente.
- **Sampling:** Se utiliza la técnica de reparametrización para muestrear del espacio latente.
- **Modelo VAE:** Implementación personalizada que calcula la pérdida de reconstrucción y la divergencia KL.

### 4. Entrenamiento
- El modelo se entrena con callbacks de EarlyStopping y reducción de tasa de aprendizaje.
- Se monitoriza la pérdida total, la pérdida de reconstrucción y la divergencia KL durante el entrenamiento.

### 5. Visualización de Resultados
- Se grafican las pérdidas para analizar el aprendizaje del modelo.
- Se generan nuevas imágenes de rostros a partir de muestras aleatorias del espacio latente.
- Se comparan imágenes originales con sus reconstrucciones para evaluar la calidad del VAE.

## ¿Cómo Funciona?

1. **Codificación:** El encoder transforma una imagen de entrada en un vector latente que representa los rasgos predominantes de la cara.
2. **Muestreo:** Se realiza una muestra aleatoria en el espacio latente para permitir la generación de nuevas caras.
3. **Decodificación:** El decoder toma el vector latente y reconstruye la imagen, conservando los rasgos principales.
4. **Manipulación:** Modificando el vector latente, es posible alterar características predominantes de la cara (por ejemplo, sonrisa, orientación, etc.).

## Estructura del Repositorio

- `autoencoders.ipynb`: Notebook principal con todo el flujo de trabajo y visualizaciones.
- `datos_kaggle/img_align_celeba/`: Carpeta con las imágenes del dataset CelebA.
- `requirements.txt`: Dependencias necesarias para ejecutar el proyecto.

## Requisitos

- Python 3.8+
- TensorFlow
- Keras
- numpy, matplotlib, pillow

Instalar dependencias:
```bash
pip install -r requirements.txt
```

## Ejecución

1. Descarga el dataset CelebA y colócalo en la ruta indicada (`datos_kaggle/img_align_celeba/img_align_celeba`).
2. Ejecuta el notebook `autoencoders.ipynb` paso a paso.
3. Explora las visualizaciones y prueba la generación y modificación de caras.

## Notas
- El modelo puede ser ajustado cambiando el tamaño del espacio latente, la arquitectura del encoder/decoder o el número de épocas.
- Las visualizaciones generadas en el notebook permiten analizar la capacidad del VAE para capturar y modificar los rasgos predominantes de los rostros.

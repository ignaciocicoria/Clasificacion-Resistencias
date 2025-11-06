# Clasificación de Resistencias

## Descripción

El objetivo del proyecto es desarrollar un algoritmo capaz de determinar el valor numérico de cada resistencia analizada. Para ello se procesan  40 imágenes de resistencias eléctricas en diferentes perspectivas, se aplica segmentación, transformaciones geométricas y detección de colores para las bandas de la resistencia.
Cada resistencia tiene 4 bandas de colores:
Las primeras 3 bandas definen el valor de la resistencia. 
La cuarta banda (siempre dorada) se debe ignorar, está ligeramente mas separada que las demas.
Se mostrará por consola el valor en Ohms de cada resistencia analizada. 


---

## Estructura del repositorio

Clasificacion-Resistencias/

│── clasificacion-resistencias.py
├── requirements.txt                      # Librerías necesarias para ejecutar el proyecto
└── README.md                             # Documentación del ejercicio

---

## Flujo del algoritmo

1. **Carga de imágenes**
   - Lectura de las imágenes desde las carpetas `data/train` y `data/test`, organizadas por clase.
   - Asignación automática de etiquetas a partir del nombre de la carpeta.

2. **Preprocesamiento**
   - Redimensionado de imágenes a un tamaño fijo (por ejemplo, 64x64).
   - Conversión a escala de grises o espacio de color adecuado (según el enfoque utilizado).
   - Normalización de intensidades.

3. **Extracción de características**
   - Aplanado de la imagen (vector de píxeles) **y/o**
   - Cálculo de descriptores (histogramas de color, momentos, etc.).

4. **Entrenamiento del clasificador**
   - División explícita entre entrenamiento y prueba (si no se usa la estructura train/test).
   - Entrenamiento de un modelo de scikit-learn (por ejemplo, k-NN, SVM, RandomForest).

5. **Evaluación**
   - Cálculo de métricas de clasificación (accuracy, precision, recall, F1-score).
   - Generación de la matriz de confusión.
   - Visualización de algunos ejemplos correctamente y erróneamente clasificados.

6. **Guardado del modelo (opcional)**
   - Serialización del modelo con `joblib` o `pickle` en la carpeta `models/`.

---

## Librerías utilizadas

Las principales librerías utilizadas para este ejercicio son:

- `opencv-python` – lectura y preprocesamiento de imágenes
- `numpy` – operaciones matriciales
- `matplotlib` – visualización de imágenes y resultados
- `scikit-learn` – modelos de clasificación y métricas
- `seaborn` (opcional) – visualización de la matriz de confusión

Ejemplo de `requirements.txt`:

opencv-python  
numpy  
matplotlib  
scikit-learn  
seaborn  

Si querés fijar versiones, podés usar algo como:

opencv-python==4.9.0.80  
numpy==1.26.4  
matplotlib==3.8.4  
scikit-learn==1.4.2  
seaborn==0.13.2  

---

## Ejecución del proyecto con entorno virtual

Desde la carpeta raíz del repositorio:

```bash
# 1) Crear entorno virtual
python -m venv venv

# 2) Activar el entorno virtual
# En Windows:
venv\Scripts\activate
# En Linux / macOS:
source venv/bin/activate

# 3) Instalar dependencias
pip install -r requirements.txt

# 4) Ejecutar el script principal
python src/clasificacion_resistencias.py

# 5) (Opcional) Desactivar el entorno virtual al finalizar
deactivate

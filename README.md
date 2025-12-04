# 🥃 Detección de Fernet con YOLOv11 🧠

Este proyecto muestra el flujo completo para **entrenar y utilizar un detector de botellas de fernet** a partir de **YOLOv11**, usando un **dataset propio anotado en Roboflow**.

---

## 🎯 **Objetivo**

- Partir de un modelo **YOLOv11n** pre-entrenado en COCO.  
- Verificar que **no reconoce** la clase *fernet* de forma nativa.  
- Crear y descargar un **dataset propio** con una sola clase: `fernet`.  
- Realizar **fine-tuning** del modelo YOLOv11n sobre ese dataset.  
- Evaluar métricas y analizar visualmente el desempeño.  
- Dejar el modelo **listo para inferencia y exportación** a otros entornos.

---

## 🧱 **Tecnologías y herramientas**

- **Python 3.12**  
- **Ultralytics YOLOv11**  
- **Roboflow** (gestión del dataset y anotaciones)  
- **Exportación a ONNX** para despliegue multiplataforma  

---

## 🗂 **Dataset**

- **Plataforma:** Roboflow  
- **Proyecto:** Detección de botellas de fernet  
- **Clase única:** `fernet`

- ---

## 🔁 **Flujo del proyecto**

### 🧩 **1. Configuración del entorno**
- Instalación de Ultralytics, Roboflow y librerías auxiliares.  
- Verificación de la GPU disponible.  

---

### 🔍 **2. Pruebas iniciales con YOLOv11 pre-entrenado**
- Inferencia sobre una imagen general para validar detecciones del dataset COCO.  
- Inferencia sobre una imagen de fernet:  
  - El modelo detecta objetos genéricos (como `bottle`), pero **no existe la clase específica `fernet`**, motivando el fine-tuning.  

---

### 📥 **3. Descarga del dataset propio desde Roboflow**
- Conexión al workspace y proyecto configurado en Roboflow.  
- Descarga del dataset en formato compatible con YOLOv11.  
- Verificación de estructura de carpetas (`train / valid / test`).  

---

### 🧬 **4. Entrenamiento (fine-tuning) de YOLOv11n**
- Entrenamiento del modelo desde pesos pre-entrenados.  
- 100 épocas de entrenamiento con imágenes de 640×640.  
- Generación automática de:  
  - Curvas de pérdida (train y valid).  
  - Curvas de **precisión**, **recall** y **mAP**.  
  - Matriz de confusión.  
  - Ejemplos de batches con etiquetas y predicciones.  

---

### 📊 **5. Evaluación y observaciones**
- Las pérdidas de entrenamiento muestran una **tendencia descendente**, señal de aprendizaje estable.  
- Las pérdidas de validación presentan un **pico intermedio**, típico en datasets pequeños.  
- Precision y recall alcanzan valores muy altos, pero deben interpretarse considerando:  
  - El tamaño reducido del set de validación.  
  - La importancia de complementar con evaluación visual.  

---

### 🧪 **6. Inferencia sobre test y nuevas imágenes**
- El modelo detecta correctamente `fernet` en las imágenes del set de test.  
- Se prueban imágenes externas:  
  - Imagen original de fernet.  
  - Imagen rotada y con umbral de confianza más alto.  
- En ambos casos, la detección es **robusta y consistente**.  

---

### 📤 **7. Exportación y uso del modelo**
- Exportación del modelo re-entrenado a **formato ONNX**, apto para:  
  - Integración en aplicaciones locales.  
  - Uso en distintos runtimes o lenguajes.  
- Además, se muestra cómo cargar el modelo entrenado desde Ultralytics para realizar inferencia programática.  

---


# 📊 Telecom X – Parte 2: Predicción de Cancelación (Churn)

**Autor:** Junior11995 (Wilfredo Rojas)  
**Notebook (Colab):** _(agrega tu enlace de Colab Parte 2)_  
**Repositorio Parte 2:** https://github.com/Junior11995/Challenge-TelecomX-Parte2-Prediccion

---

## 📌 Descripción
Este proyecto corresponde a la **Parte 2 del Challenge Telecom X (ONE + Alura LATAM)**.  
El objetivo es **predecir la evasión de clientes (churn)** a partir del dataset tratado en la Parte 1, construyendo y evaluando modelos de Machine Learning.

**Resumen del flujo:**
- Carga del dataset tratado (Parte 1).
- Preparación para ML (drop de IDs, encoding, imputación, balanceo).
- Análisis de correlación y selección de variables.
- Entrenamiento de **al menos dos modelos**:
  - Regresión Logística (con normalización).
  - Random Forest (sin normalización).
- Evaluación con métricas y conclusiones estratégicas.

---

## 🎯 Objetivos
1. Preparar y separar datos (train/test con estratificación).  
2. Tratar desbalance de clases (SMOTE).  
3. Entrenar 2+ modelos de clasificación.  
4. Evaluar con **Accuracy, Precision, Recall, F1, ROC-AUC** y **Matriz de Confusión**.  
5. Identificar **variables más influyentes** y proponer acciones de negocio.

├── data/
│ ├── telecom_clean.csv # Dataset tratado (producido en Parte 1)
│
├── notebooks/
│ ├── desaf_o_telecomx_parte2.ipynb # Notebook principal (Colab/Jupyter)
│
├── models/
│ ├── pipeline_churn_smote_lr.joblib # Pipeline (prepro + SMOTE + LR)
│ ├── pre_bal.joblib # Preprocesador (imputación + OHE + escala)
│
├── outputs/
│ ├── model_results_comparison.csv # Comparativa de métricas
│ ├── y_test.csv # y_test para reproducibilidad
│
├── README.md
└── requirements.txt


> Si usas otra estructura, actualiza las rutas en el notebook.

---

## 🛠️ Tecnologías
- **Python 3.11**
- **Pandas, NumPy** (manipulación)
- **Scikit-learn** (preprocesamiento, modelado, métricas)
- **Imbalanced-learn** (SMOTE)
- **Matplotlib, Seaborn** (visualización)
- **Joblib** (persistencia de pipelines/modelos)
- Entorno: **Google Colab / Jupyter**

---

## 🔧 Preparación de Datos (resumen)
- **Eliminación de columnas irrelevantes**: `customerid` y otros IDs.  
- **Codificación categórica**: `OneHotEncoder(handle_unknown="ignore")`.  
- **Imputación de nulos**:
  - Numéricas: `SimpleImputer(strategy="median")`
  - Categóricas: `SimpleImputer(strategy="most_frequent")`
- **Estandarización**: `StandardScaler()` **solo para modelos sensibles a escala** (p.ej., Regresión Logística).
- **Balanceo**: `SMOTE` aplicado **solo en train**.

---

## 🔍 Análisis
- **Correlación y selección de variables**:
  - Matriz de correlación con el target.
  - **Chi²** (para variables no negativas) y **ANOVA F-test**.
- **Análisis dirigido**:
  - Tiempo de contrato × Churn  
  - Gasto total × Churn  

---

## 🤖 Modelado
- **Modelo 1 (sens. a escala):** Regresión Logística (pipeline con imputación + OHE + escalado).  
- **Modelo 2 (no sens. a escala):** Random Forest (pipeline con imputación + OHE).  

**Evaluación** en test (sin reamostrar):  
- Accuracy, Precision, Recall, F1, ROC-AUC  
- Matriz de Confusión  
- Curva ROC

---

## 📈 Resultados (ejemplo esperado)
- Desbalance inicial aproximado: **~74%** no churn / **~26%** churn.  
- **Random Forest** suele ofrecer mejor **ROC-AUC** y **Recall** para la clase churn vs. LogReg.  
- Variables influyentes típicas: **tenure**, **monthlycharges/totalcharges**, tipo de **contrato** y **servicios** (internet/soporte/streaming).

*(Sustituye con tus métricas reales del notebook.)*

---

## 🚀 Ejecución
1. Clonar este repo:
   ```bash
   git clone https://github.com/Junior11995/Challenge-TelecomX-Parte2-Prediccion.git
   cd Challenge-TelecomX-Parte2-Prediccion

Instalar dependencias:

pip install -r requirements.txt


Abrir el notebook:

Google Colab: sube notebooks/desaf_o_telecomx_parte2.ipynb

Jupyter: jupyter notebook notebooks/desaf_o_telecomx_parte2.ipynb

🧠 Conclusiones y Recomendaciones

Modelo recomendado: el que logre mayor ROC-AUC y buen Recall en churn (minimiza falsos negativos).

Posibles mejoras:

Validación cruzada y ajuste de hiperparámetros (Grid/Randomized Search).

Ingeniería de variables (interacciones y transformaciones).

Monitoreo y reentrenamiento periódico con datos recientes.

👤 Autor

Junior11995 (Junior Alexis Valera)
Analista Junior de Machine Learning – Challenge ONE + Alura LATAM

---

## 🗂️ Estructura

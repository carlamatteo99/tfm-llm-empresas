# Factores asociados a la aparición de empresas en respuestas generadas por modelos de lenguaje

TFM — Carla Mateo Cansino

El objetivo de este trabajo es ver si hay factores que expliquen por qué unos modelos de lenguaje (ChatGPT y Gemini) nombran a unas empresas y a otras no. Para eso analizo variables como la presencia en Wikipedia, la similitud semántica entre la web de la empresa y las respuestas del modelo, o el número de menciones en distintas consultas.

---

## Estructura del proyecto

tfm-llm-empresas/

│

├── Extracción del contenido web de las empresas del estudio PART1.ipynb

├── Análisis_estadístico CARLAMATEO.ipynb

├── requirements.txt

│

├── consultas/

│   ├── GPT.pdf          # Respuestas de ChatGPT a las 5 consultas

│   └── GEMINI.pdf       # Respuestas de Gemini a las 5 consultas

│

└── notebook_y_corpus/

├── corpus_final.csv                  # Textos web de las empresas

└── datos_empresas_definitivo.xlsx    # Dataset con todas las variables

## Notebooks

### 1. Extracción del contenido web (`PART1.ipynb`)

Extrae el texto de las páginas web de las 28 empresas del estudio usando Selenium y BeautifulSoup. El resultado es el corpus (`corpus_final.csv`) que se usa en el análisis.

### 2. Análisis estadístico (`Análisis_estadístico CARLAMATEO.ipynb`)

Aquí está todo el análisis. Incluye:

- Embeddings con Sentence-BERT y similitud coseno
- Correlaciones de Spearman y Mann-Whitney
- Tests exactos de Fisher
- Modelos de clasificación: regresión logística, MLP, SVM, Random Forest y Gradient Boosting
- Validación leave-one-out, SHAP, curva ROC y t-SNE
- Comparativa entre ChatGPT y Gemini por consulta

---

## Cómo ejecutar

1. Descarga el repositorio y descomprímelo si es necesario.
2. Instala las dependencias:
```bash
   pip install -r requirements.txt
```
3. Abre Jupyter desde la carpeta `tfm-llm-empresas/` para que las rutas funcionen:
```bash
   cd tfm-llm-empresas
   jupyter notebook
```
4. Ejecuta primero el notebook de extracción y luego el de análisis.

> Los PDFs de las consultas tienen que estar en la carpeta `consultas/` para que el notebook de análisis los encuentre.

---

## Requisitos

Python 3.9 o superior. Todas las dependencias están en `requirements.txt`.

Los modelos de Sentence-BERT se descargan solos la primera vez (necesitas conexión a internet).

---

## Reproducibilidad

Se usa `seed=42` en todos los análisis con componente aleatoria para que los resultados sean los mismos cada vez que se ejecute.

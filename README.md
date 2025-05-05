# Sistema de Recuperación Aumentada por Generación (RAG) para la Primera Infancia

Este proyecto implementa un sistema de **Recuperación Aumentada por Generación (RAG)** enfocado en brindar respuestas confiables a preguntas frecuentes relacionadas con el desarrollo en la primera infancia, utilizando fuentes científicas y oficiales en español e inglés.

## Objetivo

Ofrecer un sistema automatizado que asista a padres, madres y cuidadores con información clara y basada en evidencia científica, aprovechando tecnologías modernas de procesamiento de lenguaje natural (PLN) como embeddings multilingües, recuperación semántica y generación con modelos LLM.

---

## Tecnologías y herramientas

- `LangChain`: framework del pipeline RAG
- `FAISS`: base vectorial para búsqueda semántica
- `PyMuPDF`: lectura y extracción de texto desde PDFs
- `Hugging Face`: embeddings multilingües (`paraphrase-multilingual-MiniLM-L12-v2`)
- `Groq API`: generación de respuestas con LLaMA 3 (70B)
- `Google Colab`: entorno de desarrollo
- `dotenv`: manejo de variables de entorno

---

## Estructura del proyecto

```

proyecto\_rag/
├── corpus/                    # Carpeta con documentos PDF (español/inglés)
│   └── ...
├── .env                       # Contiene tu GROQ\_API\_KEY
├── vectorstore/              # Base FAISS generada localmente
├── scripts/
│   ├── carga\_documentos.py   # Carga y chunking de PDFs
│   ├── embeddings\_faiss.py   # Generación de embeddings y base vectorial
│   ├── qa\_rag\_chain.py       # Configuración del RAG y generación de respuestas
│   └── evaluacion.py         # Métricas BERTScore y ROUGE-L
└── README.md

````

---

## Cómo ejecutar el proyecto

> Recomendado: ejecutar desde [Google Colab](https://colab.research.google.com/drive/1qIW3imwW_JShjl1W8I1pZ0fDVJE8gVTE?usp=sharing)

### 1. Clonar el repositorio
```bash
git clone https://github.com/tu_usuario/proyecto_rag_infancia.git
cd proyecto_rag_infancia
````

### 2. Instalar dependencias

```bash
pip install -r requirements.txt
```

O manualmente:

```bash
pip install langchain faiss-cpu pymupdf sentence-transformers huggingface-hub python-dotenv
pip install -U langchain-community langchain-groq tqdm evaluate transformers
```

### 3. Configurar el archivo `.env` que contiene la clave individual de API de Groq

Crear un archivo `.env` en la raíz del proyecto con el siguiente contenido:

```env
GROQ_API_KEY=la_clave_aqui
```

---

### 4. Ejecutar los scripts

* **Cargar y fragmentar documentos:**

```bash
python scripts/carga_documentos.py
```

* **Generar embeddings y guardar base FAISS:**

```bash
python scripts/embeddings_faiss.py
```

* **Ejecutar cadena RAG y hacer preguntas:**

```bash
python scripts/qa_rag_chain.py
```

* **Evaluar las respuestas generadas:**

```bash
python scripts/evaluacion.py
```

---

## Evaluación del sistema

Se evaluó el modelo con:

* **BERTScore F1**: coherencia semántica
* **ROUGE-L F1**: coincidencia estructural con respuestas esperadas

| Pregunta                  | BERTScore F1 | ROUGE-L F1 |
| ------------------------- | ------------ | ---------- |
| Cuidados básicos          | 0.744        | 0.303      |
| Estimulación del lenguaje | 0.723        | 0.311      |
| Vacunas                   | 0.798        | 0.400      |
| Lactancia                 | 0.833        | 0.414      |
| Etapas antes de caminar   | 0.761        | 0.311      |

---

## Licencia

Este proyecto está disponible bajo la licencia MIT.
Para más información, consultá el archivo `LICENSE`.

---

## 📬 Contacto

**Andrea Aguilera**
[Email](andream.aguilera.r@gmail.com) | [GitHub](ama388)

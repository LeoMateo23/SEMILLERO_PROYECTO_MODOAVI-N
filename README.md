# Asistente Inteligente para PATITO S.A.

## Descripción

Este proyecto implementa un asistente inteligente basado en **Retrieval-Augmented Generation (RAG)** utilizando **LangChain** y **Google Gemini**. El sistema responde consultas relacionadas con el catálogo de productos, las políticas comerciales y el proceso de ventas de PATITO S.A., mediante agentes especializados coordinados por un agente orquestador.

Además, incorpora un agente multimodal para el análisis de imágenes de productos, un agente de acción para registrar oportunidades comerciales y observabilidad mediante Phoenix para monitorear la ejecución del sistema.

---

# Características principales

- Arquitectura RAG.
- Agentes especializados.
- Agente orquestador.
- Base vectorial con Chroma.
- Embeddings de Google Gemini.
- Agente multimodal para análisis de imágenes.
- Agente de acción para registrar oportunidades.
- Observabilidad mediante Phoenix.
- Interfaz interactiva desarrollada con ipywidgets.

---

# Arquitectura

El sistema está compuesto por los siguientes componentes:

- Interfaz del asistente.
- Agente Orquestador.
- Agente Catálogo y Precios.
- Agente de Políticas Comerciales.
- Agente de Proceso de Ventas y CRM.
- Agente Multimodal.
- Agente de Acción.
- Bases vectoriales Chroma.
- Google Gemini.
- Phoenix.

---

# Tecnologías utilizadas

- Python 3.11
- JupyterLab
- Google Gemini
- LangChain
- LangGraph
- ChromaDB
- Phoenix
- ipywidgets
- Pillow
- Pandas

---

# Dependencias

Instalar las dependencias con:

```bash
pip install langchain
pip install langchain-google-genai
pip install langchain-community
pip install langchain-chroma
pip install chromadb
pip install pillow
pip install pandas
pip install ipywidgets
pip install python-dotenv
pip install arize-phoenix
pip install openinference-instrumentation-langchain
```

O utilizando:

```bash
pip install -q langchain langchain-google-genai langchain-community langchain-chroma chromadb pillow pandas ipywidgets python-dotenv
pip install -q arize-phoenix openinference-instrumentation-langchain
```

---

# Estructura del proyecto

```
Proyecto/
│
├── documentos/
│   ├── 01_Catalogo_Productos_Precios.txt
│   ├── 02_Politicas_Comerciales_Descuentos_Credito.txt
│   └── 03_Proceso_Ventas_CRM.txt
│
├── registro_oportunidades.txt
├── patito_pro.png
├── Proyecto_Final.ipynb
└── README.md
```

---

# Base de conocimiento

La información utilizada por el asistente proviene de tres documentos independientes:

- Catálogo de productos y precios.
- Políticas comerciales.
- Proceso de ventas y CRM.

Cada documento es dividido en fragmentos (chunks), convertido en embeddings mediante Google Gemini y almacenado en una colección independiente de Chroma.

---

# Agentes implementados

## Agente Catálogo y Precios

Responde consultas relacionadas con:

- productos;
- precios;
- disponibilidad;
- características técnicas.

---

## Agente de Políticas Comerciales

Responde consultas relacionadas con:

- descuentos;
- crédito;
- garantías;
- devoluciones;
- anticipos.

---

## Agente de Proceso de Ventas y CRM

Responde consultas sobre:

- etapas del embudo;
- registro de oportunidades;
- cierre de ventas;
- posventa.

---

## Agente Multimodal

Analiza imágenes de productos mediante Google Gemini Vision para extraer información visible como:

- nombre del producto;
- precio;
- disponibilidad;
- garantía;
- características.

---

## Agente de Acción

Permite registrar oportunidades comerciales validando previamente que toda la información requerida esté completa.

Los registros se almacenan en:

```
registro_oportunidades.txt
```

---

## Agente Orquestador

Coordina el funcionamiento del sistema.

Analiza la intención del usuario y decide qué agente especializado debe intervenir para responder la consulta o ejecutar una acción.

---

# Observabilidad

El proyecto utiliza **Phoenix** para registrar automáticamente:

- llamadas al modelo Gemini;
- consultas a los retrievers;
- herramientas ejecutadas;
- tiempos de respuesta;
- consumo de tokens;
- trazas completas de ejecución.

---

# Flujo de funcionamiento

1. El usuario realiza una consulta.
2. El orquestador identifica la intención.
3. Se selecciona el agente correspondiente.
4. El retriever recupera el contexto desde Chroma.
5. Google Gemini genera la respuesta.
6. Si corresponde, el agente de acción registra la oportunidad.
7. Phoenix registra toda la ejecución.

---

# Ejemplos de consultas

### Catálogo

- ¿Cuál es el precio del Patito Pro 2026?
- ¿Qué accesorios están disponibles?

### Políticas

- ¿Qué descuento puede autorizar un vendedor?
- ¿Cuál es la política de devoluciones?

### CRM

- ¿Qué requisitos existen para marcar una oportunidad como ganada?
- ¿Cuáles son las etapas del embudo de ventas?

### Multimodal

- Analiza la imagen `patito_pro.png`.

### Acción

- Registra una oportunidad para Comercial ABC con 10 unidades del Patito Pro 2026.

---

# Autores
- Ashley Huanca 
- María Alvarado 
- Leonardo Yugsan 


Proyecto desarrollado como parte del Proyecto Final de la asignatura de Inteligencia Artificial / Sistemas Inteligentes.

Universidad de Guayaquil.


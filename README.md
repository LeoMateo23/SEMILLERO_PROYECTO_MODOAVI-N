# 🤖 Asistente Inteligente para PATITO S.A.

## Proyecto Final – Semillero de Inteligencia Artificial

### Grupo: Modo Avión ✈️

**Universidad de Guayaquil**

**Integrantes**
- Ashley Huanca
- María Alvarado
- Leonardo Yugsan

---

# 📖 Descripción

Este proyecto desarrolla una **Mesa de Ayuda Inteligente** para el departamento de Ventas de **PATITO S.A.**, implementada mediante una arquitectura **Retrieval-Augmented Generation (RAG)** y un sistema **multiagente**. La solución integra modelos de lenguaje de Google Gemini, bases vectoriales con Chroma y herramientas de acción para responder consultas, analizar imágenes y registrar oportunidades comerciales.

El sistema fue desarrollado íntegramente en **JupyterLab**, incorporando una interfaz interactiva construida con `ipywidgets`, un agente orquestador para coordinar agentes especializados y un mecanismo de observabilidad mediante **Arize Phoenix**, que permite monitorear el comportamiento del sistema, las llamadas al modelo, el uso de herramientas y las métricas de ejecución.

---

# 🎯 Objetivo

Diseñar e implementar una Mesa de Ayuda Inteligente capaz de asistir al departamento de Ventas de PATITO S.A. mediante la recuperación de información empresarial, el análisis multimodal y la automatización de tareas comerciales, empleando una arquitectura RAG con agentes especializados.

---

# ✨ Características Principales

- Arquitectura basada en **Retrieval-Augmented Generation (RAG)**.
- Agente Orquestador para coordinar agentes especializados.
- Agentes independientes para Catálogo, Políticas Comerciales y CRM.
- Agente Multimodal para análisis de imágenes.
- Agente de Acción para registrar oportunidades de venta.
- Bases vectoriales independientes utilizando Chroma.
- Embeddings generados con Google Gemini.
- Interfaz gráfica interactiva desarrollada en JupyterLab con `ipywidgets`.
- Observabilidad completa mediante Arize Phoenix.
- Persistencia local del registro de oportunidades comerciales.
---
---

# 🏗️ Arquitectura de la Solución

El asistente inteligente está organizado mediante una arquitectura **multiagente**, donde un **Agente Orquestador** analiza cada consulta y delega la tarea al agente especializado correspondiente. Los agentes utilizan bases de conocimiento independientes mediante **RAG** y, cuando es necesario, herramientas de acción para ejecutar operaciones sobre los datos.

```text
                           Usuario
                              │
                              ▼
                 Interfaz del Asistente
                     (ipywidgets)
                              │
                              ▼
                  Agente Orquestador
      ┌─────────────┼─────────────┬─────────────┬─────────────┐
      ▼             ▼             ▼             ▼             ▼
  Catálogo      Políticas        CRM      Multimodal      Acción
      │             │             │             │             │
      └─────────────┴─────────────┴─────────────┴─────────────┘
                              │
                              ▼
              Google Gemini + Chroma + Tools
                              │
                              ▼
                    Respuesta al Usuario
                              │
                              ▼
                Arize Phoenix (Observabilidad)
```

---

# 🧩 Arquitectura de Agentes

| Componente | Función | Implementación |
|:----------|:--------|:---------------|
| **Catálogo** | Consulta productos, precios y características. | RAG + ChromaDB |
| **Políticas** | Responde consultas sobre descuentos, créditos y garantías. | RAG + ChromaDB |
| **CRM** | Proporciona información del proceso comercial y ventas. | RAG + ChromaDB |
| **Multimodal** | Analiza imágenes de productos y documentos. | `gemini-3.1-flash-lite` |
| **Acción** | Registra oportunidades comerciales y valida información. | `@tool` + Function Calling |
| **Orquestador** | Analiza la intención y coordina los agentes especializados. | LangGraph + LangChain |
| **Observabilidad** | Monitorea la ejecución del sistema y las métricas. | Arize Phoenix |
| **Interfaz** | Permite la interacción del usuario mediante un chatbot. | `ipywidgets` + `threading` |

---

# 🔄 Flujo de Funcionamiento

1. El usuario realiza una consulta desde la interfaz del asistente.
2. El Agente Orquestador identifica la intención de la solicitud.
3. La consulta se dirige al agente especializado correspondiente.
4. El agente recupera información mediante RAG o ejecuta una herramienta de acción, según sea necesario.
5. Google Gemini genera la respuesta utilizando el contexto recuperado.
6. Si la consulta implica una operación de registro, el Agente de Acción valida la información antes de almacenarla.
7. Arize Phoenix registra la ejecución completa del sistema para su análisis.
8. La respuesta final se presenta al usuario a través de la interfaz.

---

# 🛠️ Tecnologías Utilizadas

El proyecto fue desarrollado utilizando las siguientes tecnologías y herramientas:

| Categoría | Herramienta |
|:----------|:------------|
| Lenguaje | Python 3.11 |
| Entorno de desarrollo | JupyterLab |
| Framework para LLM | LangChain |
| Orquestación de agentes | LangGraph |
| Modelo de lenguaje | Google Gemini |
| Embeddings | GoogleGenerativeAIEmbeddings |
| Base vectorial | ChromaDB |
| Observabilidad | Arize Phoenix |
| Instrumentación | OpenInference |
| Interfaz gráfica | ipywidgets |
| Procesamiento de imágenes | Pillow |
| Manipulación de datos | Pandas |
| Variables de entorno | python-dotenv |

---

# 📋 Requisitos

Para ejecutar correctamente el proyecto se requiere:

- Python 3.11 o superior.
- JupyterLab instalado.
- Una API Key válida de Google Gemini.
- Conexión a Internet.
- Git (opcional, para clonar el repositorio).

---

# 📦 Instalación

Clonar el repositorio:

```bash
git clone https://github.com/LeoMateo23/SEMILLERO_PROYECTO_MODOAVION.git
```

Ingresar al directorio del proyecto:

```bash
cd SEMILLERO_PROYECTO_MODOAVION
```

Instalar las dependencias:

```bash
pip install -q langchain langchain-google-genai langchain-community langchain-chroma chromadb pillow pandas ipywidgets python-dotenv

pip install -q arize-phoenix openinference-instrumentation-langchain
```

---

# ⚙️ Configuración

Crear un archivo `.env` en la raíz del proyecto con la siguiente variable:

```text
GOOGLE_API_KEY=TU_API_KEY
```

Una vez configurada la clave, el proyecto podrá autenticarse con los servicios de Google Gemini.

---

# 📁 Estructura del Proyecto

```text
SEMILLERO_PROYECTO_MODOAVION/
│
├── documentos/
│   ├── 01_Catalogo_Productos_Precios.txt
│   ├── 02_Politicas_Comerciales_Descuentos_Credito.txt
│   └── 03_Proceso_Ventas_CRM.txt
│
├── patito_pro.png
├── registro_oportunidades.txt
├── Proyecto_Final.ipynb
├── README.md
├── .env
└── requirements.txt (opcional)
```
---

# 📚 Base de Conocimiento

La Mesa de Ayuda IA utiliza una base de conocimiento compuesta por tres documentos independientes, cada uno orientado a un dominio específico del departamento de Ventas de PATITO S.A.

| Documento | Contenido |
|:----------|:----------|
| `01_Catalogo_Productos_Precios.txt` | Información sobre productos, precios, disponibilidad y características. |
| `02_Politicas_Comerciales_Descuentos_Credito.txt` | Políticas de descuentos, créditos, garantías, devoluciones y anticipos. |
| `03_Proceso_Ventas_CRM.txt` | Procedimientos del proceso comercial y uso del CRM. |

Cada documento se divide en fragmentos mediante la función `chunkear_por_secciones()`, preservando la estructura semántica del contenido.

Posteriormente, cada fragmento es convertido en un *embedding* utilizando Google Gemini y almacenado en una colección independiente de ChromaDB para facilitar la recuperación de información.

---

# 🧠 Arquitectura RAG

El sistema implementa una arquitectura **Retrieval-Augmented Generation (RAG)** para responder consultas basadas únicamente en la información disponible en la documentación de la empresa.

Características principales:

- Recuperación semántica mediante ChromaDB.
- Embeddings generados con Google Gemini.
- Colecciones independientes para cada dominio.
- Recuperación mediante *retrievers* especializados.
- Generación de respuestas contextualizadas con Google Gemini.
- Reducción de alucinaciones utilizando únicamente el contexto recuperado.

---

# 🤖 Agentes Implementados

## 📦 Agente de Catálogo

Especializado en consultas relacionadas con:

- Productos.
- Precios.
- Disponibilidad.
- Características técnicas.

Utiliza una base vectorial dedicada para recuperar la información correspondiente antes de generar la respuesta.

---

## 📋 Agente de Políticas Comerciales

Responde consultas sobre:

- Descuentos.
- Créditos.
- Garantías.
- Devoluciones.
- Anticipos.

La información proviene exclusivamente del documento de políticas comerciales.

---

## 📈 Agente de Proceso de Ventas y CRM

Asiste al usuario con información relacionada con:

- Etapas del embudo comercial.
- Registro de oportunidades.
- Cierre de ventas.
- Posventa.
- Buenas prácticas del CRM.

---

## 🖼️ Agente Multimodal

Este agente aprovecha las capacidades multimodales de Google Gemini para interpretar imágenes.

Su funcionamiento comprende:

1. Lectura de la imagen.
2. Conversión al formato requerido por Gemini.
3. Construcción del mensaje multimodal.
4. Envío de la imagen junto con la consulta.
5. Generación de una respuesta basada en el contenido visual.

---

## 📝 Agente de Acción

Permite registrar oportunidades comerciales mediante herramientas implementadas con `@tool`.

Antes de almacenar la información, verifica que estén presentes todos los campos obligatorios:

- Cliente.
- Contacto.
- Producto.
- Cantidad.
- Precio unitario.
- Descuento.
- Condición de pago.
- Monto total.

Si la validación es satisfactoria, el agente:

- genera un identificador único;
- registra la fecha y hora;
- almacena la información en `registro_oportunidades.txt`.

---

## 🎯 Agente Orquestador

El Agente Orquestador constituye el núcleo del sistema.

Sus responsabilidades incluyen:

- Analizar la intención de la consulta.
- Seleccionar el agente especializado adecuado.
- Coordinar la interacción entre agentes cuando una consulta requiere información de múltiples dominios.
- Consolidar la respuesta antes de entregarla al usuario.

---

# 💬 Interfaz del Asistente

La interacción con el sistema se realiza mediante una interfaz desarrollada en **JupyterLab** utilizando `ipywidgets`.

La interfaz ofrece:

- Chat interactivo.
- Entrada de texto para consultas.
- Área de visualización de respuestas.
- Procesamiento no bloqueante mediante `threading`.
- Experiencia de uso similar a un chatbot convencional.

---

# 📊 Observabilidad con Arize Phoenix

El proyecto incorpora **Arize Phoenix** para monitorear y analizar la ejecución del sistema en tiempo real.

La instrumentación se realiza mediante:

- `px.launch_app()`
- `register()`
- `LangChainInstrumentor()`

Phoenix permite visualizar:

- Llamadas realizadas al modelo Google Gemini.
- Consultas a las bases vectoriales de ChromaDB.
- Ejecución de herramientas (`@tool`).
- Tiempos de respuesta.
- Consumo de tokens.
- Trazas completas del flujo de ejecución.

Esta información facilita la depuración, el análisis del rendimiento y la validación del comportamiento de los agentes.

---

# ✅ Control de Calidad

Para mejorar la confiabilidad del sistema se implementaron las siguientes estrategias:

- Recuperación de información mediante arquitectura RAG.
- Bases vectoriales independientes para cada dominio.
- Validación de datos antes de registrar oportunidades comerciales.
- Respuestas fundamentadas únicamente en el contexto recuperado.
- Manejo de consultas fuera del dominio mediante respuestas controladas.
- Observabilidad continua mediante Arize Phoenix.

---

# ▶️ Ejecución del Proyecto

1. Abrir JupyterLab.
2. Abrir el archivo `Proyecto_Final.ipynb`.
3. Ejecutar las celdas en el orden establecido.
4. Cargar la API Key desde el archivo `.env`.
5. Inicializar Arize Phoenix.
6. Construir las bases vectoriales.
7. Crear los agentes especializados.
8. Inicializar el Agente Orquestador.
9. Ejecutar la interfaz del asistente.
10. Realizar consultas.

---

# 💡 Ejemplos de Consultas

### 📦 Catálogo

- ¿Cuál es el precio del Patito Pro 2026?
- ¿Qué accesorios están disponibles?

### 📋 Políticas Comerciales

- ¿Qué descuento puede autorizar un vendedor?
- ¿Cuál es la política de devoluciones?

### 📈 CRM

- ¿Cuáles son las etapas del proceso de ventas?
- ¿Qué requisitos existen para marcar una oportunidad como ganada?

### 🖼️ Multimodal

- Analiza la imagen `patito_pro.png`.
- Describe las características visibles del producto.

### 📝 Acción

- Registra una oportunidad para Comercial ABC por la compra de 10 unidades del Patito Pro 2026.

---

# ⚠️ Limitaciones

- El sistema responde únicamente con base en la documentación proporcionada de PATITO S.A.
- Requiere conexión a Internet para utilizar los servicios de Google Gemini.
- La persistencia de oportunidades comerciales se realiza mediante un archivo de texto local.
- El proyecto está orientado a fines académicos y de demostración.

---

# 🚀 Trabajo Futuro

Las siguientes mejoras permitirían ampliar las capacidades del sistema:

- Migrar ChromaDB a una base vectorial administrada en la nube.
- Implementar autenticación y control de acceso basado en roles (RBAC).
- Sustituir el almacenamiento local por una base de datos relacional.
- Incorporar caché semántica para consultas frecuentes.
- Desplegar el sistema como aplicación web utilizando Streamlit o FastAPI.
- Integrar nuevos agentes especializados para otras áreas de la empresa.

---

# 📄 Licencia

Este proyecto fue desarrollado con fines exclusivamente académicos como parte del Proyecto Final del Semillero de Inteligencia Artificial de la Universidad de Guayaquil.

Su contenido puede utilizarse como material de referencia con la correspondiente atribución a sus autores.

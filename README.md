# Asistente Inteligente para PATITO S.A.
## Proyecto Final – Grupo Modo Avión

---

# Descripción

El presente proyecto implementa un asistente inteligente basado en la arquitectura **Retrieval-Augmented Generation (RAG)** utilizando **LangChain**, **Google Gemini** y **Chroma**.

El sistema permite responder consultas relacionadas con el catálogo de productos, políticas comerciales y proceso de ventas de PATITO S.A., además de analizar imágenes de productos y registrar oportunidades comerciales mediante un agente de acción.

El proyecto incorpora observabilidad utilizando **Arize Phoenix**, lo que permite visualizar el flujo completo de ejecución del sistema.

---

# Características principales

- Arquitectura RAG.
- Cinco agentes especializados.
- Agente Orquestador.
- Bases vectoriales independientes con Chroma.
- Embeddings de Google Gemini.
- Agente Multimodal.
- Agente de Acción.
- Observabilidad mediante Phoenix.
- Interfaz gráfica desarrollada con ipywidgets.
- Implementación completa en JupyterLab.

---

# Arquitectura de la solución

El sistema está compuesto por los siguientes componentes:

```
Usuario
      │
      ▼
Interfaz del Asistente (ipywidgets)
      │
      ▼
Agente Orquestador
      │
      ├──────────────┐
      │              │
      ▼              ▼
Agente         Agente
Catálogo       Políticas
      │
      ▼
Agente CRM
      │
      ▼
Agente Multimodal
      │
      ▼
Agente de Acción
      │
      ▼
Google Gemini + Chroma
      │
      ▼
Respuesta al usuario
      │
      ▼
Phoenix (Observabilidad)
```

---

# Flujo de funcionamiento

1. El usuario realiza una consulta mediante la interfaz.
2. El Agente Orquestador identifica la intención.
3. El orquestador selecciona uno o más agentes especializados.
4. Cada agente consulta su base vectorial mediante un retriever.
5. Google Gemini genera la respuesta utilizando el contexto recuperado.
6. Si la consulta requiere registrar una oportunidad, el Agente de Acción valida los datos y almacena la información.
7. Phoenix registra toda la ejecución del sistema.
8. La respuesta final es enviada al usuario.

---

# Tecnologías utilizadas

- Python 3.11
- JupyterLab
- LangChain
- LangGraph
- Google Gemini
- GoogleGenerativeAIEmbeddings
- Chroma
- Arize Phoenix
- OpenInference
- Pillow
- Pandas
- ipywidgets
- python-dotenv

---

# Dependencias

Instalar todas las dependencias con:

```bash
pip install -q langchain langchain-google-genai langchain-community langchain-chroma chromadb pillow pandas ipywidgets python-dotenv

pip install -q arize-phoenix openinference-instrumentation-langchain
```

---

# Requisitos

Para ejecutar correctamente el proyecto se requiere:

- Python 3.11 o superior.
- JupyterLab.
- API Key de Google Gemini.
- Conexión a Internet.

---

# Configuración

Crear un archivo `.env` con la siguiente variable:

```text
GOOGLE_API_KEY=TU_API_KEY
```

---

# Instalación

Clonar el repositorio:

```bash
git clone <[URL_DEL_REPOSITORIO](https://github.com/LeoMateo23/SEMILLERO_PROYECTO_MODOAVI-N)>
```

Ingresar a la carpeta del proyecto:

```bash
cd proyecto_modo_avión
```

Instalar las dependencias indicadas anteriormente.

---

# Estructura del proyecto

```
proyecto_modo_avión/
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
└── .env
```

---

# Base de conocimiento

La base de conocimiento está formada por tres documentos independientes:

- Catálogo de Productos y Precios.
- Políticas Comerciales.
- Proceso de Ventas y CRM.

Cada documento se divide en fragmentos mediante la función `chunkear_por_secciones()`.

Posteriormente:

- se generan embeddings utilizando Google Gemini;
- se crea una colección independiente en Chroma;
- cada colección dispone de su propio retriever.

---

# Parámetros de Ingeniería RAG

- Arquitectura: Retrieval-Augmented Generation (RAG).
- Embeddings: GoogleGenerativeAIEmbeddings.
- Vector Store: Chroma.
- Recuperación: Retriever independiente para cada base de conocimiento.
- Chunking: División de documentos por secciones mediante `chunkear_por_secciones()`.

---

# Agentes implementados

## Agente Catálogo y Precios

Responde consultas sobre:

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

Responde consultas acerca de:

- etapas del embudo;
- registro de oportunidades;
- cierre de ventas;
- posventa.

---

## Agente Multimodal

Analiza imágenes de productos utilizando la capacidad multimodal de Google Gemini.

Proceso:

1. Lectura de la imagen.
2. Conversión a Base64.
3. Construcción del mensaje multimodal.
4. Envío de imagen y prompt a Gemini.
5. Extracción de información visible del producto.

---

## Agente de Acción

Permite registrar oportunidades comerciales.

Antes del registro valida que existan todos los datos obligatorios.

Campos requeridos:

- Cliente.
- Contacto.
- Producto.
- Cantidad.
- Precio unitario.
- Descuento.
- Condición de pago.
- Monto total.

Una vez validada la información:

- genera un identificador único;
- registra fecha y hora;
- almacena la información en `registro_oportunidades.txt`.

---

## Agente Orquestador

El Agente Orquestador coordina todo el sistema.

Analiza la intención del usuario y determina qué agente especializado debe intervenir.

Dependiendo de la consulta puede utilizar:

- Catálogo.
- Políticas.
- CRM.
- Multimodal.
- Acción.

Finalmente consolida la información y entrega una única respuesta al usuario.

---

# Control de calidad

Para mejorar la confiabilidad del sistema se implementaron las siguientes medidas:

- Los agentes responden únicamente utilizando el contexto recuperado mediante RAG.
- No se inventa información cuando esta no existe en la base de conocimiento.
- El Agente de Acción valida todos los datos antes de registrar una oportunidad.
- Las consultas fuera del dominio son identificadas y respondidas apropiadamente.

---

# Observabilidad con Phoenix

El proyecto incorpora Arize Phoenix para registrar automáticamente la ejecución del sistema.

La instrumentación utiliza:

- `px.launch_app()`
- `register()`
- `LangChainInstrumentor()`

Phoenix permite visualizar:

- llamadas al modelo Gemini;
- consultas a Chroma;
- ejecución de herramientas;
- tiempos de respuesta;
- consumo de tokens;
- trazas completas del sistema.

---

# Ejecución del proyecto

1. Abrir JupyterLab.
2. Abrir `Proyecto_Final.ipynb`.
3. Ejecutar las celdas en el orden establecido.
4. Inicializar Google Gemini.
5. Inicializar Phoenix.
6. Construir las bases vectoriales.
7. Crear los agentes.
8. Ejecutar la interfaz del asistente.
9. Realizar consultas.

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

### Multimodal

- Analiza la imagen `patito_pro.png`.

### Acción

- Registra una oportunidad para Comercial ABC por la compra de 10 unidades del Patito Pro 2026.

---

# Autores

Proyecto desarrollado por el **Grupo Modo Avión**.

**Universidad de Guayaquil**

**Proyecto Final**

# Autores
- Ashley Huanca 
- María Alvarado 
- Leonardo Yugsan 

Proyecto desarrollado por el grupo **Modo Avión** como parte del Proyecto Final del Semillero de Inteligencia Artificial.

**Grupo:** Modo Avión

**Periodo académico:** 2026 - 2027

Universidad de Guayaquil.


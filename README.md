# Proyecto Final - Semillero Modo Avion

Este repositorio contiene la documentacion, datos de entrada y el codigo fuente para el desarrollo del proyecto final de analisis de datos, integracion de informacion y automatizacion de procesos comerciales.


Objetivo del Proyecto

El objetivo principal de este trabajo es procesar, estructurar y analizar la informacion de ventas, catalogos de productos y registros de clientes para evaluar el rendimiento de las operaciones comerciales y aplicar reglas de negocio predefinidas.


Descripcion detallada del proceso realizado

Paso 1: Recopilacion e ingesta de datos
Se integraron los archivos de texto que contienen la informacion base del sistema. Esto incluye la lectura de catalogos de productos con sus respectivos precios, las politicas comerciales vigentes, los flujos del proceso CRM y los registros de pedidos y oportunidades.

Paso 2: Limpieza y estandarizacion de la informacion
Se realizo una revision de los datos de entrada para detectar inconsecuencias, corregir formatos de texto y valores numéricos, eliminar espacios innecesarios y estructurar los registros de manera que puedan ser procesados analiticamente sin errores.

Paso 3: Aplicacion de reglas de negocio y politicas comerciales
Utilizando las definiciones establecidas en las politicas de descuentos y reglas comerciales, se cruzaron los datos de los pedidos con el catalogo para validar precios finales, calcular montos totales y aplicar las condiciones correspondientes a cada oportunidad.

Paso 4: Procesamiento y analisis en Jupyter Notebook
En el archivo principal Proyecto_final.ipynb se ejecutaron todas las transformaciones, cruces de tablas y calculos estadisticos. Se utilizaron librerias de procesamiento de datos en Python para automatizar el flujo de trabajo completo.

Paso 5: Generacion de resultados y recursos visuales
Como etapa final, se consolidaron las metricas clave del proceso y se generaron elementos graficos representativos para facilitar la interpretacion de los resultados obtenidos durante el analisis.


Estructura del Repositorio

- Proyecto_final.ipynb: Cuaderno Jupyter interactivo con el codigo Python, explicaciones paso a paso y ejecucion de los analisis.
- 01_Catalogo_Productos_Precios.txt: Archivo de datos con el listado de productos, identificadores y precios unitarios.
- 02_Politicas_Comerciales_Descuentos.txt: Documento con las reglas de negocio, escalas de descuentos y condiciones de venta.
- 03_Proceso_Ventas_CRM.txt: Especificacion del flujo de trabajo y estados dentro del pipeline de ventas.
- pedidos_patito.txt: Registro detallado de los pedidos ingresados para pruebas de procesamiento.
- registro_oportunidades.txt: Base de datos con el historial de oportunidades gestionadas.
- patito_pro.png: Diagrama visual y recurso grafico del modelo de datos o proceso.


Requisitos para la ejecucion

Para replicar y ejecutar el analisis en un entorno local se requiere:
- Python 3.8 o superior
- Entorno de Jupyter Notebook o VS Code
- Librerias de Python: pandas, matplotlib, numpy


Autores
Ashley Huanca 
María Alvarado 
Leonardo Yugsan 

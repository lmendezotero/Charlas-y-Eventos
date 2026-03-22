# Power Platform Madrid - Data Entry en Microsoft Fabric
Repositorio para guardar el contenido mostrado durante la charla de Data Entry en Microsoft Fabric para el evento online de Power Platform Madrid, celebrado el 26 de marzo de 2026.

![alt text](https://github.com/lmendezotero/Charlas-y-Eventos/blob/main/PPM%20-%20Translytical%20Task%20Flows%20/Imagenes/Fondo%20PPM%20Repo.png)

## Descripción del proyecto 🔊
El objetivo principal del proyecto es poner a prueba las capacidades del artefacto de Fabric Data Agent, un nuevo componente en fase de previuw lanzado por Microsoft.

Para ello, ha sido necesario realizar una serie de acciones para poder poner a prueba al agente de datos desarrollado en el presente proyecto. En primer lugar, se han analizado datos financieros de una empresa de distribución de productos de madera situada en el noroeste de España (Maderas del Noroeste). En el conjunto de datos se ha incluido información de clientes, región y localización, productos y jerarquía de categoría y subcategoría, cuentas contables. Además, se han incluido tablas de hechos de movimientos contables con inforamación de ingresos y gastos. 

Los datos de Maderas del Noroeste están almacenados en un sistema de almacenamiento en Fabric de lago de datos (Lakehouse) y las transformaciones de los datos se han realizado con notebooks de Pyspark.

Posteriormente, se ha desarrollado un informe en Microsoft Power BI facilitar el análisis financiero de la compañía, permitiendo visualizar ingresos y gastos, explorar volumetría de ventas por cliente, producto y región, así como obtener una visión global de la situación financiera del negocio mediante indicadores clave.

Por último, se ha implementado un agente de datos, llamado "Financial Analyst Assistant" con el objetivo de facilitar la consulta interactiva de la información financiera, responder preguntas en lenguaje natural y apoyar la toma de decisiones mediante el acceso ágil a los datos procesados en Fabric.

## Estructura de carpetas & Contenido 📋
El material de este repositorio está dividido en 4 carpetas principales:

### 1. Datos 📂
Nos encontramos una serie de ficheros csv que almacen la información financiera de la empresa ficticia Atlantic Woods. Estos ficheros se cargarán a una base de datos SQL de Fabric y se usarán para componer el modelo de datos del informe de Power BI. 

### 2. ETL en Fabric 📂
Detalle de la ETL realizada para obtener la estructura final de tablas y modelo de datos en el Data Warehouse del proyecto (base de datos SQL de Fabric)

Por una parte, se proporciona un archivo .zip con la exportación de una  **canalización de Data Factory** en Microsoft Fabric. Esta canalización orquesta la ejecución de tres Dataflows Gen2, diseñados para la ingesta de datos desde ficheros Excel alojados en SharePoint hacia la base de datos de destino.
Los Dataflows incluidos son:
* Dataflow de Dimensiones: Encargado de la carga de tablas de dimensiones a partir de ficheros Excel almacenados en SharePoint. 
* Dataflow de Hechos (ingresos y gastos): Encargado de la carga de tablas de datos de hechos (real/actual) a partir de ficheros Excel almacenados en SharePoint, incluyendo información financiera correspondiente a los ejercicios 2023–2024 y 2025. 
* Dataflow de Presupuesto (ingresos y gastos): Encargado de la carga de tablas de datos de hechos (presupuesto) a partir de ficheros Excel almacenados en SharePoint, incluyendo información financiera correspondiente a los ejercicios 2023–2024 y 2025. 

Por otra parte, se incluyen scripts en Python que complementan el proceso ETL mediante transformaciones más avanzadas:
* Transform Fact Actual Data: Script orientado a la transformación de datos de hechos (datos reales), preparando la información para su integración en el modelo analítico final.
* Transform Fact Budget Data: Script encargado de procesar y enriquecer la información presupuestaria, aplicando lógica de negocio específica para su análisis.
Cálculo de datos de presupuesto

### 3. User Data Functions 📂
Notebooks (lenguaje python) con el detalle del código desarrollado para dar de alta las User Data Functions (y lograr así ejecutar operaciones de CRUD para Translytical Task Flows en Fabric):
- DataFunction_BudgetData.ipynb -> Notebook desarrollado para la creación, actualización, consulta y eliminación de información presupuestaria, encapsulando la lógica de negocio mediante User Data Functions.
- DataFunction_Dimens.ipynb -> Notebook desarrollado para la gestión de tablas de dimensiones, implementando User Data Functions que permiten su integración en los Translytical Task Flows.

### 4. Power BI Report 📂
Se almacena en fichero pbix con el informe desarrollado en Power BI.

## Agradecimientos 🙏🏻

Agradecerle a la comunidad de Power Platform Madrid la oportunidad de haber podido participar como ponente en la charla online de **Data Entry en Microsoft Fabric** y aportar mi pequeño grano de arena a la comunidad. 

Dejo enlace de MeetUp de la comunidad para que estéis informandos de novedades y futuros eventos:

[Power Platform Madrid](https://www.meetup.com/es-es/power-platform-madrid/).

## Autores ✒️
* **Lorena Méndez Otero** - [lmendezotero](https://github.com/lmendezotero) 

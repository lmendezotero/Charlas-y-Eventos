# Power Platform Madrid - Data Entry en Microsoft Fabric
Repositorio para guardar el contenido mostrado durante la charla de Data Entry en Microsoft Fabric para el evento online de Power Platform Madrid, celebrado el 26 de marzo de 2026.

## Descripción del proyecto 🔊
El objetivo principal de este proyecto es explorar y demostrar las capacidades de los Translytical Task Flows en Microsoft Fabric, con el fin de habilitar operaciones de tipo CRUD (Create, Read, Update, Delete) directamente sobre los datos dentro del ecosistema Fabric, sin necesidad de recurrir a herramientas externas de entrada o mantenimiento de datos.

Este enfoque busca replicar funcionalidades típicas de aplicaciones externas de data entry, pero integradas de forma nativa en Fabric, permitiendo simplificar la arquitectura, reducir dependencias y mantener todo el ciclo de vida del dato dentro de una única plataforma.

Para alcanzar este objetivo, se han llevado a cabo las siguientes acciones:

* **Diseño e implementación de la capa de almacenamiento**. Se ha creado una base de datos SQL en Microsoft Fabric, requisito fundamental para habilitar el uso de Translytical Task Flows.
* **Construcción del modelo de datos**. Mediante canalizaciones y Dataflows, se han ingestado y transformado los datos para generar tablas de hechos y dimensiones. Adicionalmente, se han desarrollado procesos ETL en Python para enriquecer y depurar la información, obteniendo un modelo de datos optimizado para análisis y operación.
* **Desarrollo de User Data Functions (UDFs)**. Se han implementado funciones específicas que permiten exponer capacidades transaccionales sobre el modelo de datos (concretamente sobre tablas de dimensiones y la tabla de hechos de presupuesto del modelo de datos).
* **Integración con Power BI para escenarios translytical**. Finalmente, se ha desarrollado un informe en Power BI conectado al modelo analítico, desde el cual es posible interactuar con los datos y ejecutar operaciones de mantenimiento (creación, actualización y eliminación de registros) en tiempo casi real, validando así el uso de Translytical Task Flows en un escenario práctico.

En conjunto, este proyecto demuestra cómo Microsoft Fabric puede evolucionar desde una plataforma puramente analítica hacia un entorno translytical, capaz de soportar tanto análisis como operaciones transaccionales sobre los datos.

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

Agradecerle a la comunidad de **Power Platform Madrid** la oportunidad de haber podido participar como ponente en la charla online de **Data Entry en Microsoft Fabric** y aportar mi pequeño grano de arena a la comunidad. 

Dejo enlace de MeetUp de la comunidad para que estéis informandos de novedades y futuros eventos:

[Power Platform Madrid](https://www.meetup.com/es-es/power-platform-madrid/).

## Autores ✒️
* **Lorena Méndez Otero** - [lmendezotero](https://github.com/lmendezotero) 

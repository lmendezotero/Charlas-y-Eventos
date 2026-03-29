# W4TT-DataAgents

Repositorio para guardar el contenido mostrado durante la charla de Agentes de IA en Fabric para el evento de Women For Technical Talks (WFTT), celebrado los días 7 y 8 de noviembre de 2025.

![alt text](https://github.com/lmendezotero/W4TT-DataAgents/blob/main/Imagenes/Logo%20Largo%20W4TT.png)

## Descripción del proyecto 🔊
El objetivo principal del proyecto es poner a prueba las capacidades del artefacto de Fabric Data Agent, un nuevo componente en fase de previuw lanzado por Microsoft.

Para ello, ha sido necesario realizar una serie de acciones para poder poner a prueba al agente de datos desarrollado en el presente proyecto. En primer lugar, se han analizado datos financieros de una empresa de distribución de productos de madera situada en el noroeste de España (Maderas del Noroeste). En el conjunto de datos se ha incluido información de clientes, región y localización, productos y jerarquía de categoría y subcategoría, cuentas contables. Además, se han incluido tablas de hechos de movimientos contables con inforamación de ingresos y gastos. 

Los datos de Maderas del Noroeste están almacenados en un sistema de almacenamiento en Fabric de lago de datos (Lakehouse) y las transformaciones de los datos se han realizado con notebooks de Pyspark.

Posteriormente, se ha desarrollado un informe en Microsoft Power BI facilitar el análisis financiero de la compañía, permitiendo visualizar ingresos y gastos, explorar volumetría de ventas por cliente, producto y región, así como obtener una visión global de la situación financiera del negocio mediante indicadores clave.

Además, se ha implementado un agente de datos, llamado "Financial Analyst Assistant" con el objetivo de facilitar la consulta interactiva de la información financiera, responder preguntas en lenguaje natural y apoyar la toma de decisiones mediante el acceso ágil a los datos procesados en Fabric.

Por último, se ha conectado el Agente de Fabric a la herramienta de Copilot Studio para poder publicarlo en un chat de Microsoft Teams para que sea más amigable para el usuario explorar los datos y consumir el agente.

## Estructura de carpetas & Contenido 📋
El material de este repositorio está dividido en 4 carpetas principales:

### Datos 📂
Nos encontramos una serie de ficheros csv que almacen la información financiera de la empresa Maderas del Noroeste. Estos ficheros se cargarán al Lakehouse y se usarán para componer el modelo de datos del informe de Power BI. 

### Notebooks 📂
Notebooks de Pyspark desarrollados en Fabric para realizar las siguientes acciones:
- DimTablesToDelta.ipynb -> Notebook desarrollado para transformar los datos de dimensiones de los ficheros csv a tablas delta y almacenarlos en el Lakehouse.
- FactTablesToDelta.ipynb -> Notebook desarrollado para transformar los datos de hechos de los ficheros csv a tablas delta y almacenarlos en el Lakehouse.
- FDA Evaluation.ipynb -> Notebook desarrollado para evaluar el grado de acierto en las respuestas obtenidas por el agente a través del SDK.
- FDA Interaction with programming.ipynb -> Notebook desarrollado para probar la iteracción del SDK con el agente.

### Power BI 📂
Se almacena en fichero pbix con el informe desarrollado en Power BI.

### Fabric Data Agent 📂
Se almacena información relevante para el agente de datos (prompting, ejemplos de queries sql, etc).

## Agradecimientos 🙏🏻

Agradecerle a la comunidad de Women For Technical Talks la oportunidad de haber podido participar como ponente en el evento de **10º evento online anfitrionas: hablemos de tecnología** y aportar mi pequeño grano de arena a la comunidad. 

Dejo enlace de la página web oficial para que estéis informandos de novedades y futuros eventos:

[Women For Technical Talks](https://www.women4tt.com/).

## Autores ✒️

* **Lorena Méndez Otero** - [lmendezotero](https://github.com/lmendezotero) 

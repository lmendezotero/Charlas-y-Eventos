# Power Platform Madrid - Análisis Precio Vivienda con Fabric y MCP
Repositorio para guardar el contenido mostrado durante la charla de "Del dato público a la IA: Analiznado el precio de la vivienda con Fabric y MCP" para el evento presencial de Power Platform Madrid, celebrado el 9 de mayo de 2026 en las instalaciones de la Universidad Europea (Alcobendas, Madrid).

## Descripción del proyecto 🔊
El objetivo principal de este proyecto es explorar y evaluar las capacidades del MCP Core Cloud de Microsoft Fabric como herramienta de automatización y asistencia al desarrollo dentro de proyectos de analítica de datos.

Para ello, se ha desarrollado un caso práctico centrado en el análisis del precio de la vivienda en España, utilizando datos públicos procedentes de fuentes oficiales e inmobiliarias.
* Evaluación del índice de previos de la vivienda (IPC): [Web INE](https://www.ine.es/dyngs/INEbase/es/operacion.htm?c=Estadistica_C&cid=1254736152838&idp=1254735976607&menu=ultiDatos&utm_source=chatgpt.com)
* Extracciónde preciosvivos de vivenda (compraventa y alquiler): [Web Idealista](https://www.idealista.com/sala-de-prensa/informes-precio-vivienda/)
* Extracción de operaciones de compraventa registradas (1): [Web Registro Propiedad](https://www.registradores.org/actualidad/portal-estadistico-registral/estadisticas-de-propiedad?utm_source=chatgpt.com)
* Extracción de operaciones de compraventa registradas (2): [Web Datos Abietos del Gobierno](https://datos.gob.es/es/catalogo/a16003011-estadistica-registral-inmobiliaria-2025?utm_source=chatgpt.com)

Para alcanzar este objetivo, se han llevado a cabo las siguientes acciones:
* Obtención y procesamiento de datos públicos relacionados con precios de compraventa, alquiler y operaciones inmobiliarias.
* Desarrollo de notebooks en Python para realizar tareas de limpieza, transformación y enriquecimiento de datos.
* Uso de MCP Cloud junto con GitHub Copilot para automatizar la creación y gestión de elementos de Microsoft Fabric, como Lakehouses, notebooks, Dataflows y pipelines, directamente desde Visual Studio Code mediante lenguaje natural.
* Construcción de una arquitectura analítica en Fabric basada en Lakehouse, utilizando Dataflows y procesos ETL para estructurar la información.
* Desarrollo de un informe en Power BI conectado al Lakehouse, incorporando métricas DAX y visualizaciones para analizar la evolución del mercado inmobiliario español.

Este proyecto permite validar cómo MCP Cloud puede acelerar tareas de ingeniería de datos y reducir trabajo operativo dentro del ecosistema Fabric, especialmente en las fases iniciales de desarrollo y configuración de proyectos analíticos.

## Requisitos necesarios para arrancar 🛠️
* Cuenta de Microsoft Entra ID (profesional o educativa) con permisos de Fabric.
* Acceso a Microsoft Fabric: una instancia de Fabricactiva con al menos un espacio de trabajo al que pueda acceder (F2 o superior).
* Agente compatible con MCP: VS Code con GitHub Copilot o Claude Desktop.

## Instalación de Software - Agregar MCP Core Cloud Fabric en VS Code 🖥️

*VS Code (Recommendado)*
Compatible tanto con las versiones Stable como Insiders de VS Code.
* Instala la [extensión](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat&utm_source=chatgpt.com) de GitHub Copilot Chat.
* Instala la [extensión](https://marketplace.visualstudio.com/items?itemName=fabric.vscode-fabric-mcp-server&utm_source=chatgpt.com) de Fabric MCP Server.

*Agregar Servidor MCP Principal de Fabric Core*

1. En VS Code, presione Ctrl+Mayús+P (o Cmd+Mayús+P en macOS) para abrir la paleta de comandos.

2. Escriba MCP: Agregar servidor y seleccione HTTP en la lista.

3. Escriba la dirección URL del servidor MCP de Fabric Core:

  https://api.fabric.microsoft.com/v1/mcp/core

4. Cuando se le solicite un nombre de servidor, escriba fabric.

5. VS Code abre el explorador para la autenticación. Inicie sesión con su cuenta de Microsoft Entra ID. La ventana del explorador se cierra automáticamente después de la autenticación correcta.

6. Revise la conexión del servidor MCP desde VS Code. En VS Code, abra gitHub Copilot Chat presionando Ctrl+Alt+I (o Cmd+Alt+I en macOS) y escriba el siguiente mensaje:

```json
List all my Fabric workspaces
```

A continuación, se debería ver una lista de nombres de áreas de trabajo a las que tiene acceso.

## Configuración MCP Manual en VS Code
También se puede configurar el servidor MCP Core de Fabric editando directamente el archivo de configuración de VS Code. Agregue lo siguiente a .vscode/mcp.json:

```json
{
  "servers": {
    "fabric": {
      "type": "http",
      "url": "https://api.fabric.microsoft.com/v1/mcp/core"
    }
  }
}
```



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

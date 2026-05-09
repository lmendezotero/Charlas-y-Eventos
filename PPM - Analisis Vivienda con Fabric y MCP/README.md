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

2. Escriba **MCP: Agregar servidor** y seleccione HTTP en la lista.

3. Escriba la dirección URL del servidor MCP de Fabric Core:

```json
https://api.fabric.microsoft.com/v1/mcp/core
```

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
Nos encontramos una serie de ficheros CSV procesados que serán utilizados como origen de datos del proyecto. Los datasets han sido limpiados y transformados mediante Python antes de su carga en Microsoft Fabric, donde serán utilizados para construir el modelo analítico y el informe de Power BI orientado al análisis del precio de la vivienda en España.

### 2. ETL en Fabric 📂
Detalle de la ETL realizada para obtener la estructura final de tablas y modelo de datos en el Data Lakehouse del proyecto (base de datos SQL de Fabric). Para la preparación y explotación analítica de los datos, se han desarrollado distintos procesos ETL utilizando notebooks en Python dentro de Microsoft Fabric.

Por una parte, se han implementado notebooks específicos para el tratamiento de datasets procedentes de distintas fuentes relacionadas con el mercado inmobiliario español:
- Índice de Precios de Vivienda (IPV) del INE
- Datos de precios de oferta de Idealista
- Estadísticas del Registro de la Propiedad

Por otra parte, se han desarrollado notebooks para la generación de las tablas analíticas del proyecto, siguiendo un enfoque dimensional orientado a explotación en Power BI:
- Tablas de dimensiones (fechas, geografía, tipologías, indicadores, etc.)
- Tablas de hechos con métricas inmobiliarias y estadísticas del sector vivienda

Estas tablas son posteriormente cargadas en el Lakehouse de Microsoft Fabric y utilizadas como base del modelo semántico y del informe analítico desarrollado en Power BI.

### 4. Power BI Report 📂
Se almacena en fichero pbix con el informe desarrollado en Power BI para el análisis del precio del vivienda.

## Agradecimientos 🙏🏻

Agradecerle a la comunidad de **Power Platform Madrid** la oportunidad de haber podido participar como ponente en la charla online de **Data Entry en Microsoft Fabric** y aportar mi pequeño grano de arena a la comunidad. 

Dejo enlace de MeetUp de la comunidad para que estéis informandos de novedades y futuros eventos:

[Power Platform Madrid](https://www.meetup.com/es-es/power-platform-madrid/).

## Autores ✒️
* **Lorena Méndez Otero** - [lmendezotero](https://github.com/lmendezotero) 

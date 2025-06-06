# Capítulo VI: Product Implementation, Validation & Deployment.

La implementación, validación y despliegue del producto son esenciales para asegurar que la visión del producto se convierta en una realidad funcional y accesible para nuestros usuarios. Estas etapas nos permiten transformar el diseño conceptual en una aplicación real, probada y lista para su uso, lo que nos ayuda a validar nuestras ideas, identificar posibles problemas y ofrecer una experiencia de usuario óptima.

## 6.1. Software Configuration Management.

La gestión de la configuración del software es crucial para nuestro trabajo, ya que nos permite mantener un control preciso sobre los elementos de nuestro proyecto, como el código fuente, los documentos de diseño y los activos digitales. Esto garantiza que todos los miembros del equipo estén trabajando con la misma versión de los archivos y facilita la colaboración entre desarrolladores, diseñadores y otros profesionales involucrados en el proyecto. En esta sección, se detalla la configuración de ambiente de desarrollo del software, como también el planeamiento, desarrollo y evidencia de los sprints.

### 6.1.1. Software Development Environment Configuration.

A modo de asegurar un ciclo de vida de nuestro producto de Software, utilizamos una gran cantidad de instrumentos para asegurar un buen manejo del projecto, especificación de requerimientos de forma detallada y ordenada, un diseño de producto responsivo y coherente, y un desarrollo de software con buenas prácticas y colaborativo. A continuación, se presentan y justifican las herramientas adoptadas para el desarrollo de Macetech:

- #### Project Management:

  - ### Jira Software:
    Jira Software es una herramienta de gestión de proyectos ágil utilizada por equipos para planificar, rastrear, lanzar y dar soporte a software. Funciona como una fuente centralizada de información para el ciclo de vida completo del desarrollo, permitiendo a los equipos autónomos trabajar rápidamente mientras se mantienen conectados con los objetivos generales del negocio. Es ampliamente utilizada para el seguimiento de incidencias y la gestión de proyectos, ofreciendo funcionalidades como tableros Scrum y Kanban, líneas de tiempo para planificación y seguimiento, informes integrados e integraciones con miles de aplicaciones.
    <br>
    <img src="/assets/img/capitulo-6/logos/jira-logo.png" width="200px" height="200px" alt="Jira Software Logo"></img> 
    <br>
    En SevenSync se utilizó Jira Software a partir de la plantilla "Scrum". Esta plantilla nos permitió elaborar el product backlog priorizado y planear las historias de usuario que se incluyen en cada iteración de sprint. Debido a que Jira cuenta con un dashboard accesible y de claro entendimiento, se agilizaron los procesos de designación de tareas entre los miembros del equipo lo cuál permitió un desarrollo ágil de software.
    <img src="/assets/img/capitulo-6/evidence/jira-evidence.png" alt="Evidencia de Uso en Jira"></img>
    <br>Referencia: Atlassian. (s.f.). Get Started with Jira - Comprehensive Beginner's Guide. Recuperado de https://www.atlassian.com/software/jira/guides/getting-started/introduction <br>
  - ### Discord:
    Discord es una aplicación de comunicación gratuita que permite a decenas de millones de personas hablar y pasar el rato con sus comunidades, creadores y amigos favoritos. Está centrada en la gestión de comunidades y ofrece herramientas de comunicación como llamadas de voz y video, salas de chat persistentes, mensajes directos, grupos personales e integraciones con otros servicios.
  <br>
    <img src="/assets/img/capitulo-6/logos/discord-logo.jpg" width="250px" height="200px" alt="Discord Logo"></img>
  <br>
    Discord fue el medio de comunicación principal del equipo al contar con canales de texto y voz. En el grupo de discord "SevenSync - IOT", se recuerda constantemente las tareas pendientes, se marcan pautas y guías para desarrollar artefactos de calidad y se realiza el desarrollo de la documentación y software de forma simultánea. De esta manera, aseguramos la comunicación del equipo en todo momento para que todos estén al tanto del ciclo de vida del proyecto.
         <img src="/assets/img/capitulo-6/evidence/discord-evidence.png" alt="Evidencia de Uso en Discord"></img>
    <br>Referencia: Discord. (s.f.). What is Discord?. Recuperado de https://discord.com/creators/what-is-discord 

  - ### Excalidraw: 
    Excalidraw es una pizarra colaborativa en línea, de código abierto y gratuita, diseñada para crear diagramas, ilustraciones y diagramas de flujo con un estilo dibujado a mano. Se caracteriza por su simplicidad, facilidad de uso y enfoque en la privacidad y seguridad. Ofrece un lienzo infinito y herramientas esenciales para esbozar ideas rápidamente, siendo útil para reuniones, brainstorming, diagramación y prototipos rápidos.   
    <br>
    <img src="/assets/img/capitulo-6/logos/excalidraw-logo.jpg" width="200px" height="200px" alt="Excalidraw Logo"></img> <br>

    Se utilizó esta herramienta para que el equipo realice sesiones de brainstorming, diseño colaborativo y explicación visual de ideas o conceptos complejos.
       <img src="/assets/img/capitulo-6/evidence/excalidraw-evidence.png" alt="Evidencia de Uso en Excalidraw"></img>
    <br>Referencia: Excalidraw. (s.f.). Excalidraw | Online whiteboard collaboration made easy. Recuperado de https://excalidraw.com/
   
  - ### Whatsapp: 
    WhatsApp es una aplicación de mensajería y llamadas utilizada por más de 2 mil millones de personas en más de 180 países para mantenerse en contacto con amigos y familiares. Permite enviar y recibir una variedad de archivos multimedia (texto, fotos, videos, documentos y ubicación), así como realizar llamadas de 1  voz. Se caracteriza por ser simple, segura y confiable, ofreciendo cifrado de extremo a extremo en las comunicaciones.
    <br>
    <img src="/assets/img/capitulo-6/logos/whatsapp-logo.png" width="200px" height="200px" alt="Whatsapp Logo"></img> <br>
    El equipo creó un grupo de Whatsapp para la comunicación rápida y accesible fuera del entorno de trabajo principal, coordinaciones y para avisos urgentes.
    <img src="/assets/img/capitulo-6/evidence/whatsapp-evidence.png" alt="Evidencia de Uso en Whatsapp"></img>

    <br> Referencia: WhatsApp. (s.f.). Acerca de nosotros. Recuperado de https://www.whatsapp.com/about?lang=es

  - ### Google docs:
    Google Docs es un procesador de texto en línea que permite crear y editar documentos, así como colaborar en tiempo real con otros usuarios. Almacena los documentos en la nube (Google Drive), ahorrando espacio en el dispositivo local. Ofrece funcionalidades de formato de texto y párrafo, inserción de imágenes, tablas, enlaces, revisión ortográfica y gramatical, control de cambios y la posibilidad de trabajar sin conexión.
    <br>
    <img src="/assets/img/capitulo-6/logos/google-docs-logo.jpg" width="200px" height="200px" alt="Google docs Logo"></img> <br>
    
    Hemos utilizado Google Docs para hacer seguimiento de las responsabilidades del equipo y poder asignar una calificación correspodiente en base a la entrega a tiempo, la colaboración constante y las entregas realizadas.<br>

     <img src="/assets/img/capitulo-6/evidence/google-docs-evidence.png" alt="Evidencia de Uso en Google Docs"></img>
    Referencia: Google Workspace. (s.f.). Google Docs: Online Document & PDF Editor. Recuperado de https://workspace.google.com/products/docs/
- #### Requirement Management:
  - ### Miro:
       <br>
       Miro es una plataforma de pizarra colaborativa en línea que permite a los equipos trabajar juntos en tiempo real. Ofrece una variedad de plantillas y herramientas para brainstorming, mapeo mental, diagramación, planificación ágil, gestión de proyectos y más, funcionando como un espacio visual centralizado para la colaboración.

      <img src="/assets/img/capitulo-6/logos/miro-logo.jpg" width="200px" height="200px" alt="Miro Logo"></img>
      Hemos utilizado Miro para sesiones de brainstorming iniciales, mapeo de funcionalidades relacionadas con los Bounded Contexts y quizás para estructurar flujos de usuario o diagramas de planificación visual.
<img src="/assets/img/capitulo-6/evidence/miro-evidence.png" alt="Evidencia de Uso en Miro"></img>
      Referencia: Miro. (s.f.). The online collaborative whiteboard platform. Recuperado de https://miro.com/


    
  - ### UXPressia:
       <br>
       UXPressia es una plataforma de experiencia del cliente (CX) y experiencia del usuario (UX) que se especializa en la creación de Customer Journey Maps, Personas de Usuario e Impact Maps. Permite visualizar y comprender la experiencia del usuario a través de diferentes puntos de contacto.
      
      <img src="/assets/img/capitulo-6/logos/uxpressia-logo.jpg" width="200px" height="200px" alt="Ux Pressia Logo"></img>
    
      Hemos utilizado UXPressia para definir a nuestros usuarios objetivo creando Personas detalladas y para mapear sus interacciones clave con el sistema a través de Customer Journey Maps, ayudando a centrar el diseño en las necesidades del usuario.
    <img src="/assets/img/capitulo-2/needfinding/user-persona/UserPerson1.png" alt="Evidencia de Uso en UXPressia"></img>

Referencia: UXPressia. (s.f.). Customer Experience & User Experience Platform. Recuperado de https://uxpressia.com/

  - ### Structurizr:
  Structurizr es una herramienta diseñada para crear modelos de software utilizando el enfoque C4 (Context, Container, Component, Code). Permite visualizar la arquitectura de un sistema en diferentes niveles de abstracción, facilitando la comunicación arquitectónica dentro del equipo.
      <img src="/assets/img/capitulo-6/logos/structurizr-logo.jpg" width="200px" height="200px" alt="Structurizr Logo"></img>
Hemos utilizado Structurizr para modelar y documentar la arquitectura del sistema, representando cómo interactúan los distintos Bounded Contexts (como IAM, Pot Management, etc.) y sus componentes internos.

Referencia: Structurizr. (s.f.). Visualise, document and explore your software architecture. Recuperado de https://structurizr.com/
     <img src="/assets/img/capitulo-6/evidence/Structurizr-evidence.jpeg" alt="Evidencia de Uso en Structurizr"></img>
- #### Product UX/UI Design:
  - ### Figma:
  Figma es un editor de diseño de interfaces colaborativo basado en la nube. Permite a los equipos diseñar, prototipar y compartir interfaces de usuario para aplicaciones web y móviles en tiempo real. Ofrece herramientas vectoriales, componentes reutilizables y capacidades de prototipado interactivo.
    <img src="/assets/img/capitulo-6/logos/figma-logo.jpg" width="200px" height="200px" alt="Figma Logo"></img>
Hemos utilizado Figma para diseñar las interfaces de usuario de la aplicación, incluyendo wireframes, mockups y prototipos interactivos para funcionalidades como el registro, inicio de sesión, gestión de macetas y visualización de datos.
      <img src="/assets/img/capitulo-6/evidence/figma-evidence.png" alt="Evidencia de Uso en Figma"></img>

Referencia: Figma. (s.f.). The Collaborative Interface Design Tool. Recuperado de https://www.figma.com/

  - ### LucidChart:
  Lucidchart es un espacio de trabajo visual que permite crear diagramas de flujo, diagramas de red, organigramas, mapas mentales y otros tipos de diagramas para visualizar ideas, sistemas y procesos. Ofrece funcionalidades de colaboración y una amplia biblioteca de formas.
<img src="/assets/img/capitulo-6/logos/lucidchart-logo.jpg" width="200px" height="200px" alt="Structurizr Logo"></img>
Hemos utilizado Lucidchart para crear diagramas complementarios al diseño UX/UI y a la arquitectura, como flujos de usuario detallados, diagramas de procesos o diagramas conceptuales del sistema.
     <img src="/assets/img/capitulo-5/ux-ui-design/user-flow/UserFlow-1.png"></img>
Referencia: Lucidchart. (s.f.). Your visual workspace. Recuperado de https://www.lucidchart.com/

- #### Software Development:

  - ### HTML5:
    Es un lenguaje de etiquetado utilizado para crear la estructura de páginas web. Lo utilizamos para incluir componentes como texto, imágenes, enlaces, botones y videos en nuestras páginas web. En este proyecto, HTML5 fue utilizado para definir la estructura y los elementos de las interfaces de usuario en el frontend, como formularios, dashboards y listas de macetas o plantas.
    
    <img src="/assets/img/capitulo-6/evidence/html-evidence.png" alt="Evidencia de Uso de HTML5"></img>
  - ### CSS:
    Un lenguaje de diseño gráfico utilizado para dar formato y estilo a la presentación de un documento escrito en HTML.Hemos utilizado CSS para aplicar estilos visuales a los elementos HTML, asegurando que la interfaz de usuario se vea limpia y coherente con el diseño establecido. <br>
     <img src="/assets/img/capitulo-6/evidence/css-evidence.png" alt="Evidencia de Uso de CSS"></img>
  - ### JavaScript:
     Un lenguaje de programación orientado a objetos dinámico que utilizamos para implementar funcionalidades en un documento HTML. JavaScript ha sido fundamental para añadir interactividad a la aplicación, manejar eventos del usuario, realizar validaciones en el cliente y comunicarse con los servicios backend a través de APIs.
    <img src="/assets/img/capitulo-6/evidence/js-evidence.png" alt="Evidencia de Uso de JavScript"></img>
  - ### WebStorm:
    Un entorno de desarrollo integrado (IDE) que emplearemos para trabajar con JavaScript.
    Utilizamos WebStorm como nuestro IDE principal para el desarrollo frontend, aprovechando sus herramientas de edición, depuración y gestión de código para HTML, CSS y JavaScript.
    [Link De Descarga](https://www.jetbrains.com/es-es/webstorm/)
    <img src="/assets/img/capitulo-6/evidence/webstorm-evidence.png" alt="Evidencia de Uso de WebStorm"></img>

  - ### Rider
    Rider es un entorno de desarrollo integrado (IDE) creado por JetBrains, diseñado específicamente para el desarrollo .NET utilizando lenguajes como C#, F# y VB.NET, y también soporta desarrollo con Unity. Ofrece un conjunto completo de herramientas para codificación, depuración, pruebas unitarias y refactorización.

- #### Software Documentation:
  - ### Github:
  
    GitHub es una plataforma basada en la nube que permite almacenar, compartir y colaborar en la escritura de código con otras personas. Utiliza el sistema de control de versiones Git y facilita el seguimiento y la gestión de cambios en el código a lo largo del tiempo. Es un espacio centralizado para proyectos de desarrollo de software que fomenta la colaboración entre equipos.
    <br>

    <img src="/assets/img/capitulo-6/logos/github-logo.jpg" width="200px" height="200px" alt="Github Logo"></img> <br>
    
    GitHub es fundamental como repositorio centralizado para el código fuente y documentación. Nos permitió manejar el control de versiones, la colaboración segura entre múltiples mimebros del equipo trabajando en paralelo (mediante ramas y pull requests), la revisión de código y el seguimiento de cambios. Es la herramienta clave para mantener el código del equipo sincronizado y gestionado de forma colaborativa.
    <br>
    <img src="/assets/img/capitulo-6/evidence/github-evidence.png" alt="Evidencia de Uso en Github">
    <br>Referencia: GitHub Docs. (s.f.). About GitHub and Git. Recuperado de https://docs.github.com/en/get-started/start-your-journey/about-github-and-git

- #### Software Deployment:
  - ### GitHub Pages:
    Una plataforma que posibilita la realización de despliegues simples directamente desde un repositorio de GitHub. <br>

    Referencia:       
    <img src="/assets/img/capitulo-6/evidence/github-pages-evidence.png" alt="Evidencia de Uso de Github Pages">

### 6.1.2. Source Code Management.



- #### GitFlow Implementation:

  Para implementar el flujo de trabajo Gitflow utilizando Git como nuestra herramienta de control de versiones, nos basamos en la entrada de blog "A successful Git branching model" de Vincent Driessen. Esta referencia nos permitió establecer las convenciones detalladas que serán aplicadas en nuestro proyecto
   <img src="/assets/img/capitulo-6/evidence/gitflow-evidence.png" alt="Evidencia de GitFlow">

- ### **Master o Main branch**

  La rama principal de desarrollo del proyecto es la Master branch. En esta rama reside el código que actualmente se encuentra en producción.

  - #### Notación: master o main

- ### **Develop branch**

  La rama "Develop" albergará las más recientes actualizaciones y cambios agregados que serán incluidos en la próxima versión del proyecto. Esta rama sirve como un espacio para la integración y prueba continua de los cambios antes de ser fusionados con la rama principal "Master" para su despliegue en producción.

  - #### Notación: develop

- ### **Feature branch**

  Las ramas de características (Feature branches) serán empleadas para desarrollar nuevas funcionalidades o características del producto que se agregarán en la siguiente versión o en versiones futuras. Estas funcionalidades deberán fusionarse eventualmente con la rama Develop.
  <br>Debe derivarse de la rama Develop.
  <br>Debe fusionarse de vuelta a la rama Develop.

  - #### Notación: release

### **Conventional Commits**

"Conventional Commits" es una convención para estructurar los mensajes de confirmación (commits) en un formato estándar y semántico. Este formato ayuda a comunicar claramente los cambios realizados en el código y facilita la generación de registros de cambios automáticos. Los "Conventional Commits" suelen seguir un formato que incluye un encabezado, un cuerpo opcional y un pie de página opcional, y se utilizan para describir de manera sucinta y clara los cambios realizados en el código, lo que facilita su seguimiento y comprensión por parte de los desarrolladores y otros miembros del equipo.
<br>
La estructura de un commit debe seguir las siguientes pautas:

```
git commit -m “<type>[optional scope]: <title>“ -m “<description”
```

**Tipos De Conventional Commits**

```
1. feat: Used to describe a new feature or functionality added to the code.
2. fix: Indicates a bug fix or solution to a problem.
3. docs: Employed for changes or improvements in code documentation.
4. style: Describes changes related to the code's formatting, such as whitespace, indentation, etc., that do not affect its functionality.
5. refactor: Used for modifications to the code that do not fix bugs or add new features, but rather improve its structure or readability.
6. test: Indicates the addition or modification of unit tests or functional tests.
7. chore: Used for changes in the build process or maintenance tasks that are not directly related to the code itself.
8. perf: Describes performance improvements in the code.
```

### 6.1.3. Source Code Style Guide & Conventions.

Como norma general, se espera que todo el código desarrollado por los miembros del equipo esté completamente redactado en inglés.

- ### HTML
  - #### Use Lowercase Element Names:
    Es recomendable utilizar minúsculas o lowercase para los nombres de los elementos HTML.
    ```
    <body>
        <p>This is a paragraph</p>
    <body>
    ```
  - #### Close All HTML Elements:
    Es recomendable cerrar todos los elementos HTML correctamente.
    ```
    <body>
        <p>This is a paragraph</p>
        <p>This is another paragraph</p>
    <body>
    ```
  - #### Use Lowercase Attribute Names:
    Es recomendable utilizar minúsculas para los nombres de los atributos HTML.
    ```
    <a href="https://www.w3schools.com/html/">Visit our HTMLtutorial</a>
    ```
  - #### Always Specify alt, width, and height for Images:
    Es recomendable seguir estas convenciones en caso de que la imagen no se pueda mostrar, lo que ayuda a mejorar la accesibilidad del contenido.
    ```
    <img src="html5.gif" alt="HTML5"
    style="width:128px;height:128px">
    ```
  - #### Spaces and Equal Signs:
    Se recomienda no utilizar espacios en blanco entre las entidades para mejorar la legibilidad.
    ```
    <link rel="stylesheet" href="styles.css">
    ```
- ### CSS
  - #### ID and Class Naming
    Es recomendable utilizar nombres de clases e id's significativos que expresen claramente el propósito del elemento.
    ```
    #gallery {}
    #login {}
    .video {}
    ```
  - #### ID and Class Name Style
    Se recomienda utilizar nombres cortos para nombrar ids o clases, pero lo suficientemente descriptivos para entender su propósito.
    ```
    #nav {}
    .author {}
    ```
  - #### Shorthand Properties
    Se recomienda utilizar propiedades CSS de forma abreviada siempre que sea posible para hacer el código más eficiente y comprensible.
    ```
    border-top: 0;
    font: 100%/1.6 palatino, georgia, serif;
    padding: 0 1em 2em;
    ```
  - #### 0 and Units
    Es recomendable evitar especificar la unidad después del valor 0 en propiedades que lo permitan, ya que esto ayuda a reducir el tamaño del código y mejora su legibilidad.
    ```
    margin: 0;
    padding: 0;
    ```
  - #### Declaration Order
    Se recomienda ordenar las declaraciones en orden alfabético para facilitar el mantenimiento y la recordación del código.
    ```
     background: fuchsia;
     border: 1px solid;
     border-radius: 4px;
     color: black;
     text-align: center;
     text-indent: 2em;
    ```
- ### Typescript
  - #### Use expanded syntax
    Cada línea de TypeScript debería estar en una nueva línea, con la llave de apertura en la misma línea de su declaración y la llave de cierre en una nueva línea al final.
    ```
    function myFunc() {
     console.log('Hello!');
    };
    ```
  - #### Variable naming
    Para el nombre de las variables, se recomienda utilizar lowerCamelCase.
    ```
    let playerScore = 0;
    let speed = distance / time;
    ```
  - #### Declaring variables
    Para la declaración de variables, es recomendable utilizar las palabras reservadas let y const en lugar de var.
    ```
    const myName = 'Chris';
    console.log(myName);
    let myAge = '40';
    myAge++;
    console.log('Happy birthday!');
    ```
  - #### Function naming
    Para el nombre de las funciones, se recomienda utilizar lowerCamelCase.
    ```
    function sayHello() {
    alert('Hello!');
    };
    ```
- ### C#
  #### Nomenclatura:
  PascalCase: Tipos (Clases, Enums, Interfaces I), Miembros Públicos/Internos (Propiedades, Métodos, Eventos), Namespaces, Constantes.
  camelCase: Variables locales, Parámetros de método, Campos privados (sin _).
  Nombres de archivo: Coincidir con el tipo público principal.
  Formato:
  #### Indentación: 4 espacios (no tabuladores).
  Llaves {}: En nueva línea (estilo Allman o similar).
  Espaciado: Un espacio alrededor de operadores, después de comas, antes de { en control de flujo. No espacios después de ( o antes de ).
  Líneas en blanco: Para separar secciones lógicas.
  Longitud de línea: Idealmente <= 120 caracteres.
  ##### Comentarios:
  ///: Documentación XML para tipos y miembros públicos/internos.
  //: Aclarar lógica compleja.
  ##### Organización:
  using: Arriba, fuera del namespace, ordenadas alfabéticamente.
  Miembros de tipo: Campos -> Constructores -> Propiedades -> Métodos -> Eventos (ordenar por visibilidad dentro de cada grupo).
  #### Buenas Prácticas:
   Usar var apropiadamente, interpolación $"", LINQ, manejo de excepciones, async/await, operadores ?. y ??.
  Herramientas: Usar .editorconfig y Analizadores Roslyn (ej. StyleCop) para automatizar y verificar el estilo.


### 6.1.4. Software Deployment Configuration.

- Despliegue Landing Page:<br> 
   <img src="/assets/img/capitulo-6/evidence/github-pages-evidence.png" alt="Evidencia de Uso de Github Pages">

- Despliegue Front End App:<br> Microsoft azure


- Despligue de FAKE API: 
   <img src="/assets/img/capitulo-6/evidence/beeceptor-api-evicende.jpeg" alt="Evidencia de Beeceptor API ">

Enlace: https://macetech.free.beeceptor.com
## 6.2. Landing Page, Services & Applications Implementation.

La implementación de la página estática de negocio, los servicios y las aplicaciones es un paso fundamental en nuestro proceso de desarrollo. Nos permite materializar el diseño y la funcionalidad planificados, transformando los conceptos en productos tangibles y listos para su uso. Esta fase nos permite traducir las especificaciones y requisitos en código, desarrollando la estructura de la página, los servicios y las aplicaciones de acuerdo con las necesidades identificadas.

### 6.2.1. Sprint 1

El primer sprint es un hito importante en nuestro proceso de desarrollo ágil. Durante este período, nos enfocamos en la implementación de las características y funcionalidades prioritarias identificadas en la planificación inicial. Esto implica traducir los requisitos y especificaciones en código funcional, desarrollando las bases de nuestro producto de manera iterativa.

#### 6.2.1.1.Sprint Planning 1.

El sprint planning es una reunión en la metodología ágil donde el equipo planifica las actividades del próximo sprint. Define qué trabajo se hará, cuánto tiempo tomará y quién será responsable. El objetivo es establecer un plan claro y alcanzable para el equipo, fomentando la colaboración y asegurando que todos estén alineados en cuanto a objetivos y prioridades.

<table  style="text-align: center;">
    <tbody>
        <tr>
			<td colspan="1">Sprint #</td>
            <td colspan="1"> Sprint 1  </td>
		</tr>
        <tr>
			<td colspan="2">Sprint Planning Background </td>
		</tr>
        <tr>
			<td colspan="1">Date</td>
            <td colspan="1"> 2025-05-09 </td>
		</tr>
        <tr>
			<td colspan="1">Time</td>
            <td colspan="1"> 01:00 PM </td>
		</tr>
        <tr>
			<td colspan="1">Location</td>
            <td colspan="1">Discord (Reunion virtual)</td>
		</tr>
        <tr>
			<td colspan="1">Prepared By</td>
            <td colspan="1"> Yen Cerna, Lucio Heli - Team Leader</td>
		</tr>
        <tr>
			<td colspan="1"> Attendees (to planning meeting)</td>
            <td colspan="1">Mallma Quispe, Rubén Elías; Pescorán Ángulo, Juan Fabritzzio; Paredes Zapata, Luiggi Gianfranco; Sanchez Zamora,
Fabrizio Alessandro; Trigueros Chumacero, Flavio Eduardo; Yen Cerna, Lucio Heli
 </td>
		</tr>
         <tr>
			<td colspan="1">Sprint 1 – 1 Review Summary </td>
            <td colspan="1">El sprint 1 se enfocó en establecer las bases iniciales de la plataforma web. Durante este periodo fundacional, el equipo logró completar la página de aterrizaje, implementar las funcionalidades esenciales de registro e inicio de sesión integradas con un fake API en Beeceptor, asegurar que el diseño fuera adaptable a diversos dispositivos y desarrollar las primeras pantallas para interactuar con la maceta inteligente. Los miembros del equipo encontraron el sprint productivo y motivador al ver el progreso inicial, mientras que el Team Leader (Prooduct Owner) se mostró muy satisfecho con los resultados, destacando la solidez de la base construida y la efectividad del enfoque adoptado para este inicio de proyecto.</td>
		</tr>
         <tr>
			<td colspan="1">Sprint 1 – 1 Retrospective Summary </td>
            <td colspan="1">Tras completar el primer Sprint, el equipo sintió que colaboraron bien y se adaptaron a los desafíos iniciales del proyecto, lo cual fue un comienzo coomplicado pero con buen descenlace. Sin embargo, también identificaron áreas clave para mejorar la forma de trabajar en el futuro, como organizar mejor los tiempos, coordinar las tareas compartidas de manera más eficiente, asegurar que siempre se enfoquen en entregar lo más valioso para el producto, y tener más reuniones cortas para mantenerse mejor comunicados y alineados en los próximos sprints.</td>
		</tr>
         <tr>
			<td colspan="2">Sprint Goal & User Stories </td>
		</tr>
         <tr>
			<td>Sprint 1 Goal</td>
            <td><strong>Nuestro enfoque es</strong> entregar una experiencia digital unificada que comunique efectivamente el valor de Macetech desde el primer contacto hasta la interacción inicial con la plataforma. <strong>Creemos que esto proporciona</strong> claridad inmediata sobre los beneficios del producto a través de una Landing Page persuasiva, y empodera a los usuarios mediante dashboards funcionales con datos simulados que generan confianza en la solución. <strong>Esto se confirmará cuando</strong> los visitantes completen acciones clave en la Landing Page (registro o descarga), los usuarios registrados naveguen intuitivamente entre los dashboards de macetas y métricas simuladas, y las pruebas de usuario demuestren comprensión del valor propuesto y capacidad para interpretar los datos presentados.
</td>
		</tr>
        <tr>
			<td colspan="1">Sprint 1 Velocity </td>
            <td colspan="1">79</td>
		</tr>
        <tr>
			<td colspan="1">Sum of Story Points </td>
            <td colspan="1">79</td>
		</tr>
</tbody>
</table>

#### 6.2.1.2.Aspect Leaders and Collaborators.
| Team Member (Last Name, First Name) | GitHub Username | IAM - Leader (L) / Collaborator (C) | Pot Management - Leader (L) / Collaborator (C) | Plant Management - Leader (L) / Collaborator (C) | Watering Management - Leader (L) / Collaborator (C) | System Monitoring & Control - Leader (L) / Collaborator (C) | Data Insights & Reporting - Leader (L) / Collaborator (C) | Caring Intelligence - Leader (L) / Collaborator (C) |
|---|---|---|---|---|---|---|---|---|
| Mallma, Ruben | RubDaShen | - | C | L | - | - | - | C |
| Paredes, Luiggi | DevLuiggi | C | - | - | - | - | C | L |
| Pescorán, Juan | JuanPescoran | - | - | - | L | - | - | - |
| Sanchez, Fabrizio | Fabrizio0711 | - | L | - | - | L | C | - |
| Trigueros, Flavio | FlavioTrigueros | C | C | - | - | - | L | C |
| Yen, Lucio | LucioY250 | L | - | C | C | - | - | - |
#### 6.2.1.3.Sprint Backlog 1.

En este primer sprint, nos enfocamos en la implementación de las funcionalidades básicas de la Landing Page, incluyendo la estructura general, el diseño visual y la navegación básica, también se ha creado un reporte que muestra el ciclo de vida de todo nuestro proyecto de software. Estas características son fundamentales para establecer las bases de nuestro producto y proporcionar una experiencia de usuario sólida y coherente.
A continuación el sprint backlog 1 y el Trello donde se repartieron los trabajos:

Enlace para ingresar al Sprint Backlog para el Sprint 1: [Enlace de Jira](https://lucioyen1-1743965307909.atlassian.net/jira/software/projects/SPB/list?filter=statusCategory+%3D+Done+AND+statusCategoryChangedDate+%3E%3D+-1w&atlOrigin=eyJpIjoiMGYzM2ZmYmI4MTc1NDZlODgzNjkwYmQ0NDRjZmVjNDUiLCJwIjoiaiJ9 )

<img src="/assets/img/capitulo-6/evidence/sprint-backlog-1.png" alt="Evidencia de Sprint Backlog para sprint 1">

<table>
	<tbody>
		<tr>
			<td>Sprint #</td>
			<td colspan="7">Sprint 1</td>
		</tr>
		<tr>
			<td colspan="2">User Story</td>
			<td colspan="6">Work - Item / Task</td>
		</tr>
		<tr>
			<td>Id</td>
			<td>Title</td>
			<td>Id</td>
			<td>Title</td>
			<td>Description</td>
			<td>Estimation (Hours)</td>
			<td>Assigned To</td>
			<td>Status (To-do / In-Process / To-Review / Done)</td>
		</tr>
  </tbody>
    <tr>
      <td>US001</td>
      <td>Ver introducción atractiva</td>
      <td>T001</td>
      <td>Implementar sección hero completa</td>
      <td><strong>Como</strong> visitante de la plataforma, <strong>quiero</strong> ver una sección introductoria concisa sobre Macetech <strong>para</strong> obtener una primera impresión positiva del sistema </td>
      <td>6</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US002</td>
      <td>Entender el valor principal</td>
      <td>T002</td>
      <td>Implementar sección valor completa</td>
      <td><strong>Como</strong> visitante de la plataforma, <strong>quiero</strong> identificar y comprender la propuesta de valor central <strong>para</strong> saber si es de mi interés </td>
      <td>6</td>
      <td>Fabrizio Sanchez</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US006</td>
      <td>Iniciar sesión desde un CTA visible</td>
      <td>T003</td>
      <td>Implementar CTA login completo</td>
      <td><strong>Como</strong> visitante, <strong>quiero</strong> ver un llamado a la acción claro <strong>para</strong> acceder a funcionalidades personalizadas </td>
      <td>5</td>
      <td>Flavio Trigueros</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US003</td>
      <td>Conocer las funcionalidades clave</td>
      <td>T004</td>
      <td>Implementar sección features completa</td>
      <td><strong>Como</strong> visitante, <strong>quiero</strong> identificar las principales funcionalidades <strong>para</strong> analizar si el producto es útil en mi situación </td>
      <td>7</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US004</td>
      <td>Visualizar un video del producto</td>
      <td>T005</td>
      <td>Implementar reproductor completo</td>
      <td><strong>Como</strong> visitante, <strong>quiero</strong> ver un video demostrativo <strong>para</strong> entender mejor cómo funciona Macetech </td>
      <td>5</td>
      <td>Juan Pescorán</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US005</td>
      <td>Conocer las opciones de membresía</td>
      <td>T006</td>
      <td>Implementar sección membresías completa</td>
      <td><strong>Como</strong> visitante, <strong>quiero</strong> ver un apartado de membresías <strong>para</strong> entender beneficios por nivel </td>
      <td>6</td>
      <td>Lucio Yen</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>TS013</td>
      <td>Integrar enlace de descarga con app stores</td>
      <td>T007</td>
      <td>Implementar integración con app stores</td>
      <td><strong>Como</strong> developer, <strong>quiero</strong> integrar enlaces a tiendas oficiales <strong>para</strong> descargas seguras </td>
      <td>4</td>
      <td>Juan Pescorán</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T007.1</td>
      <td>Obtener enlaces a tiendas</td>
      <td>Identificar y verificar los enlaces correctos a las tiendas de aplicaciones.</td>
      <td>1</td>
      <td>Juan Pescorán</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T007.2</td>
      <td>Implementar botones/links en UI</td>
      <td>Añadir los elementos visuales para los enlaces de descarga en la interfaz.</td>
      <td>2</td>
      <td>Juan Pescorán</td>
      <td>Done</td>
    </tr>
     <tr>
      <td></td>
      <td></td>
      <td>T007.3</td>
      <td>Probar redirecciones</td>
      <td>Verificar que los enlaces dirijan correctamente a las tiendas de aplicaciones.</td>
      <td>1</td>
      <td>Juan Pescorán</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US009</td>
      <td>Descargar la aplicación móvil</td>
      <td>T008</td>
      <td>Implementar banners descarga completo</td>
      <td><strong>Como</strong> visitante interesado, <strong>quiero</strong> acceder al enlace de descarga <strong>para</strong> instalar la app </td>
      <td>5</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US007</td>
      <td>Conocer a los miembros del equipo</td>
      <td>T009</td>
      <td>Implementar sección equipo completo</td>
      <td><strong>Como</strong> visitante, <strong>quiero</strong> conocer quiénes desarrollan Macetech <strong>para</strong> confiar en el proyecto </td>
      <td>5</td>
      <td>Fabrizio Sanchez</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>TS012</td>
      <td>Crear endpoint para contacto</td>
      <td>T010</td>
      <td>Desarrollar endpoint RESTful</td>
      <td><strong>Como</strong> developer, <strong>quiero</strong> desarrollar un endpoint RESTful <strong>para</strong> procesar formularios de contacto </td>
      <td>8</td>
      <td>Fabrizio Sanchez</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T010.1</td>
      <td>Diseñar estructura de datos</td>
      <td>Definir el formato de los datos del formulario de contacto.</td>
      <td>2</td>
      <td>Fabrizio Sanchez</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T010.2</td>
      <td>Implementar lógica de validación</td>
      <td>Añadir validaciones en el servidor para los datos recibidos.</td>
      <td>3</td>
      <td>Fabrizio Sanchez</td>
      <td>Done</td>
    </tr>
     <tr>
      <td></td>
      <td></td>
      <td>T010.3</td>
      <td>Integrar con servicio de email</td>
      <td>Configurar el envío del contenido del formulario a una dirección de correo.</td>
      <td>3</td>
      <td>Fabrizio Sanchez</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US008</td>
      <td>Contactar al equipo de SevenSync</td>
      <td>T011</td>
      <td>Implementar formulario contacto completo</td>
      <td><strong>Como</strong> visitante, <strong>quiero</strong> poder contactar al equipo <strong>para</strong> hacer preguntas o enviar comentarios </td>
      <td>6</td>
      <td>Flavio Trigueros</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US010</td>
      <td>Visualizar información útil en el footer</td>
      <td>T012</td>
      <td>Implementar footer completo</td>
      <td><strong>Como</strong> visitante, <strong>quiero</strong> acceder a información útil en el footer <strong>para</strong> facilitar mi navegación </td>
      <td>5</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>TS011</td>
      <td>Implementar diseño responsivo</td>
      <td>T013</td>
      <td>Asegurar responsividad completa</td>
      <td><strong>Como</strong> developer, <strong>quiero</strong> implementar diseño responsivo <strong>para</strong> que la página se vea bien en cualquier dispositivo </td>
      <td>8</td>
      <td>Juan Pescorán</td>
      <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T013.1</td>
        <td>Ajustar puntos de ruptura CSS</td>
        <td>Implementar media queries y ajustar estilos para diferentes tamaños de pantalla.</td>
        <td>4</td>
        <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T013.2</td>
        <td>Probar en dispositivos</td>
        <td>Probar la interfaz en emuladores y dispositivos reales (móvil, tablet, desktop).</td>
        <td>4</td>
        <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
      <td>US014</td>
      <td>Registrar cuenta</td>
      <td>T014</td>
      <td>Formulario registro</td>
      <td><strong>Como</strong> usuario nuevo, <strong>quiero</strong> registrar una cuenta <strong>para</strong> acceder a los servicios </td>
      <td>6</td>
      <td>Lucio Yen</td>
      <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T014.1</td>
        <td>Estructura formulario</td>
        <td>Crear la estructura HTML y estilos básicos para el formulario de registro.</td>
        <td>2</td>
        <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T014.2</td>
        <td>Implementar validación</td>
        <td>Añadir validaciones de entrada del usuario en el cliente (JavaScript).</td>
        <td>2</td>
        <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T014.3</td>
        <td>Integrar con API</td>
        <td>Conectar el formulario con el endpoint de registro del fake API en Beeceptor.</td>
        <td>2</td>
        <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
      <td>US015</td>
      <td>Iniciar sesión</td>
      <td>T015</td>
      <td>Formulario login</td>
      <td><strong>Como</strong> usuario registrado, <strong>quiero</strong> iniciar sesión con mis credenciales <strong>para</strong> acceder a mi cuenta </td>
      <td>5</td>
      <td>Flavio Trigueros</td>
      <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T015.1</td>
        <td>Estructura formulario</td>
        <td>Crear la estructura HTML y estilos básicos para el formulario de inicio de sesión.</td>
        <td>1</td>
        <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T015.2</td>
        <td>Implementar validación</td>
        <td>Añadir validaciones de entrada del usuario en el cliente (JavaScript).</td>
        <td>2</td>
        <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T015.3</td>
        <td>Integrar con API</td>
        <td>Conectar el formulario con el endpoint de inicio de sesión del fake API en Beeceptor.</td>
        <td>2</td>
        <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
    <tr>
      <td>US018</td>
      <td>Cerrar sesión</td>
      <td>T016</td>
      <td>Implementar funcionalidad de cerrar sesión</td>
      <td><strong>Como</strong> usuario autenticado, <strong>quiero</strong> cerrar sesión <strong>para</strong> proteger mi cuenta </td>
      <td>3</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
     <tr>
      <td></td>
      <td></td>
      <td>T016.1</td>
      <td>Implementar lógica frontend para cerrar sesión</td>
      <td>Añadir la lógica en el cliente para manejar el evento de cerrar sesión.</td>
      <td>1</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T016.2</td>
      <td>Limpiar sesión local</td>
      <td>Remover tokens o información de sesión almacenada en el navegador.</td>
      <td>1</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T016.3</td>
      <td>Redirigir al usuario</td>
      <td>Navegar al usuario a la página de inicio o login después de cerrar sesión.</td>
      <td>1</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US036</td>
      <td>Vincular nueva maceta</td>
      <td>T017</td>
      <td>Implementar proceso de vinculación Bluetooth</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> registrar maceta vía Bluetooth <strong>para</strong> monitorear plantas </td>
      <td>8</td>
      <td>Fabrizio Sanchez</td>
      <td>To-Do</td>
    </tr>
     <tr>
      <td></td>
      <td></td>
      <td>T017.1</td>
      <td>Implementar búsqueda Bluetooth</td>
      <td>Desarrollar la funcionalidad para escanear dispositivos Bluetooth cercanos.</td>
      <td>2</td>
      <td>Fabrizio Sanchez</td>
      <td>To-Do</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T017.2</td>
      <td>Implementar conexión a maceta</td>
      <td>Establecer la conexión Bluetooth con la maceta inteligente identificada.</td>
      <td>2</td>
      <td>Fabrizio Sanchez</td>
      <td>To-Do</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T017.3</td>
      <td>Enviar credenciales WiFi</td>
      <td>Desarrollar la función para enviar la configuración de red a la maceta.</td>
      <td>2</td>
      <td>Fabrizio Sanchez</td>
      <td>To-Do</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T017.4</td>
      <td>Confirmar vinculación</td>
      <td>Mostrar feedback al usuario sobre el éxito o fallo de la vinculación.</td>
      <td>2</td>
      <td>Fabrizio Sanchez</td>
      <td>To-Do</td>
    </tr>
    <tr>
      <td>US039</td>
      <td>Eliminar maceta</td>
      <td>T018</td>
      <td>Implementar función eliminar maceta</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> desvincular maceta <strong>para</strong> dejar de recibir notificaciones </td>
      <td>5</td>
      <td>Flavio Trigueros</td>
      <td>Done</td>
    </tr>
     <tr>
      <td></td>
      <td></td>
      <td>T018.1</td>
      <td>Crear interfaz de confirmación</td>
      <td>Diseñar y desarrollar el modal o pantalla para confirmar la eliminación.</td>
      <td>1</td>
      <td>Flavio Trigueros</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T018.2</td>
      <td>Implementar llamada API eliminar</td>
      <td>Configurar la llamada al API para solicitar la eliminación de la maceta.</td>
      <td>2</td>
      <td>Flavio Trigueros</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T018.3</td>
      <td>Actualizar lista de macetas</td>
      <td>Remover la maceta eliminada de la vista del usuario.</td>
      <td>2</td>
      <td>Flavio Trigueros</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US040</td>
      <td>Reordenar macetas</td>
      <td>T019</td>
      <td>Implementar lógica reordenar macetas</td>
      <td><strong>Como</strong> usuario con múltiples macetas, <strong>quiero</strong> reorganizarlas <strong>para</strong> acceder rápido a importantes </td>
      <td>6</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
     <tr>
      <td></td>
      <td></td>
      <td>T019.1</td>
      <td>Implementar UI de arrastrar y soltar</td>
      <td>Desarrollar la interfaz que permita reorganizar las macetas visualmente.</td>
      <td>2</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T019.2</td>
      <td>Implementar lógica para actualizar orden</td>
      <td>Añadir el código para procesar el nuevo orden de las macetas.</td>
      <td>2</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T019.3</td>
      <td>Guardar nuevo orden via API</td>
      <td>Configurar la llamada al API para persistir el nuevo orden de las macetas.</td>
      <td>2</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US054</td>
      <td>Registrar planta en maceta</td>
      <td>T020</td>
      <td>Selector plantas</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> asignar planta a maceta <strong>para</strong> recibir recomendaciones </td>
      <td>6</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T020.1</td>
        <td>Obtener lista plantas</td>
        <td>Obtener la lista de plantas disponibles desde el API.</td>
        <td>3</td>
        <td>Ruben Mallma</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T020.2</td>
        <td>Implementar selector</td>
        <td>Crear la interfaz para seleccionar una planta de la lista.</td>
        <td>3</td>
        <td>Ruben Mallma</td>
        <td>Done</td>
    </tr>
    <tr>
      <td>US055</td>
      <td>Eliminar planta de maceta</td>
      <td>T021</td>
      <td>Implementar función eliminar planta</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> remover planta <strong>para</strong> liberar maceta </td>
      <td>5</td>
      <td>Lucio Yen</td>
      <td>Done</td>
    </tr>
     <tr>
      <td></td>
      <td></td>
      <td>T021.1</td>
      <td>Crear interfaz de confirmación</td>
      <td>Diseñar y desarrollar el modal o pantalla para confirmar la eliminación de la planta.</td>
      <td>1</td>
      <td>Lucio Yen</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T021.2</td>
      <td>Implementar llamada API eliminar planta</td>
      <td>Configurar la llamada al API para solicitar la eliminación de la planta de la maceta.</td>
      <td>2</td>
      <td>Lucio Yen</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T021.3</td>
      <td>Actualizar info de maceta</td>
      <td>Reflejar la eliminación de la planta en la interfaz de información de la maceta.</td>
      <td>2</td>
      <td>Lucio Yen</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US056</td>
      <td>Ver parámetros óptimos de planta</td>
      <td>T022</td>
      <td>Mostrar parámetros óptimos de planta</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> consultar rangos ideales <strong>para</strong> comparar con sensores </td>
      <td>6</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
     <tr>
      <td></td>
      <td></td>
      <td>T022.1</td>
      <td>Obtener datos parámetros óptimos</td>
      <td>Recuperar los rangos ideales de parámetros para la planta via API en Beeceptor.</td>
      <td>2</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T022.2</td>
      <td>Diseñar sección parámetros</td>
      <td>Crear la sección de la interfaz donde se mostrarán los parámetros óptimos.</td>
      <td>2</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T022.3</td>
      <td>Renderizar datos</td>
      <td>Mostrar los rangos de parámetros óptimos en la interfaz de usuario.</td>
      <td>2</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US038</td>
      <td>Ver estado de parámetros de sensores</td>
      <td>T023</td>
      <td>Dashboard sensores</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> consultar parámetros de sensor <strong>para</strong> saber si planta necesita atención </td>
      <td>7</td>
      <td>Fabrizio Sanchez</td>
      <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T023.1</td>
        <td>Obtener datos sensores</td>
        <td>Obtener los datos de los sensores desde el API del fake API en Beeceptor.</td>
        <td>3</td>
        <td>Fabrizio Sanchez</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T023.2</td>
        <td>Mostrar datos</td>
        <td>Renderizar los datos de los sensores en el dashboard (tabla o gráfico).</td>
        <td>4</td>
        <td>Fabrizio Sanchez</td>
        <td>Done</td>
    </tr>
    <tr>
      <td>US037</td>
      <td>Personalizar nombre de maceta</td>
      <td>T024</td>
      <td>Editar nombre</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> asignar nombre único <strong>para</strong> identificar fácilmente </td>
      <td>5</td>
      <td>Flavio Trigueros</td>
      <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T024.1</td>
        <td>Crear campo entrada</td>
        <td>Añadir un campo de texto para editar el nombre de la maceta.</td>
        <td>2</td>
        <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T024.2</td>
        <td>Implementar guardar</td>
        <td>Añadir la funcionalidad para guardar el nuevo nombre via API FAKE.</td>
        <td>3</td>
        <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
    <tr>
      <td>US069</td>
      <td>Recibir alertas prioritarias</td>
      <td>T025</td>
      <td>Implementar visualización de alertas prioritarias</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> que distinga urgencias <strong>para</strong> atender lo crítico </td>
      <td>7</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
     <tr>
      <td></td>
      <td></td>
      <td>T025.1</td>
      <td>Definir lógica de priorización</td>
      <td>Establecer los criterios para categorizar las alertas por prioridad en el frontend.</td>
      <td>2</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T025.2</td>
      <td>Diseñar componentes de alerta</td>
      <td>Crear los elementos visuales para mostrar las alertas de forma clara y distintiva.</td>
      <td>2</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T025.3</td>
      <td>Mostrar alertas en UI</td>
      <td>Integrar los componentes de alerta en la interfaz de usuario principal.</td>
      <td>3</td>
      <td>Ruben Mallma</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US075</td>
      <td>Recibir recomendaciones de riego personalizadas</td>
      <td>T026</td>
      <td>Panel recomendaciones</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> sugerencias ajustadas <strong>para</strong> optimizar consumo de agua </td>
      <td>6</td>
      <td>Luiggi Paredes</td>
      <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T026.1</td>
        <td>Obtener recomendaciones</td>
        <td>Obtener las recomendaciones de riego desde el fake API en Beeceptor.</td>
        <td>3</td>
        <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T026.2</td>
        <td>Mostrar recomendaciones</td>
        <td>Mostrar las recomendaciones de manera clara en la interfaz.</td>
        <td>3</td>
        <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tr>
      <td>US060</td>
      <td>Programar riegos recurrentes</td>
      <td>T027</td>
      <td>Programador riegos</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> horarios fijos <strong>para</strong> plantas con necesidades predecibles </td>
      <td>7</td>
      <td>Lucio Yen</td>
      <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T027.1</td>
        <td>Construir UI programación</td>
        <td>Crear los selectores de día y hora para programar riegos.</td>
        <td>3</td>
        <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
         <td>T027.2</td>
        <td>Implementar guardar programación</td>
        <td>Añadir la funcionalidad para guardar los horarios programados via API.</td>
        <td>4</td>
        <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
      <td>US063</td>
      <td>Riego manual</td>
      <td>T028</td>
      <td>Botón riego manual</td>
      <td><strong>Como</strong> usuario, <strong>quiero</strong> activar riego inmediato <strong>para</strong> necesidades puntuales </td>
      <td>5</td>
      <td>Juan Pescorán</td>
      <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T028.1</td>
        <td>Crear botón</td>
        <td>Añadir el botón para activar el riego manual en la interfaz.</td>
        <td>2</td>
        <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>T028.2</td>
        <td>Implementar llamada API</td>
        <td>Configurar la llamada al API FAKE para enviar la solicitud de riego.</td>
        <td>3</td>
        <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tbody>
</table>

#### 6.2.1.4.Development Evidence for Sprint Review.

En esta sección se explica y presenta los avances en implementación con relación a los productos de la solución según el alcance del Sprint: Landing Page, Web Applications, Web Services.

Primero, se mostrarán los commits más importantes para el Reporte, los cuales muestran el ciclo de vida del proyecto, y toda la información que se usó, usa y usará para el desarrollo del proyecto:

| Repository          | Branch  | Commit ID                                | Commit Message                    | Commit Message Body                        | Commited on (Date) |
| ------------------- | ------- | ---------------------------------------- | --------------------------------- | ------------------------------------------ | ------------------ |


#### 6.2.1.5.Testing Suite Evidence for Sprint Review.

Para front es Specs de angular

#### 6.2.1.6.Execution Evidence for Sprint Review.

<img src="/assets/img/capitulo-6/evidence/landing-page-evidence.jpeg" alt="Evidencia Landing page ">


#### 6.2.1.7.Services Documentation Evidence for Sprint Review.
En el alcance de este sprint, no se realizó un web service, sin embargo, a modo de simulación de datos, desplegamos una FAKE API en Beeceptor con los siguientes endpoints:
<img src="/assets/img/capitulo-6/evidence/beeceptor-api-evicende.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-1.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-2.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-3.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-4.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-5.jpeg" alt="Evidencia Landing page ">
#### 6.2.1.8.Software Deployment Evidence for Sprint Review.

Enlace de Landing Page: https://sevensync.github.io/macetech-landing/ 
<img src="/assets/img/capitulo-6/evidence/github-pages-evidence.png" alt="Evidencia Landing page ">

#### 6.2.1.9.Team Collaboration Insights during Sprint.
<img src="/assets/img/capitulo-6/evidence/landing-page-commits-evidence.jpeg" alt="Evidencia Landing page ">
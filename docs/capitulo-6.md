# Capítulo VI: Product Implementation, Validation & Deployment.

La implementación, validación y despliegue del producto son esenciales para asegurar que la visión del producto se convierta en una realidad funcional y accesible para nuestros usuarios. Estas etapas nos permiten transformar el diseño conceptual en una aplicación real, probada y lista para su uso, lo que nos ayuda a validar nuestras ideas, identificar posibles problemas y ofrecer una experiencia de usuario óptima.

## 6.1. Software Configuration Management.

La gestión de la configuración del software es crucial para nuestro trabajo, ya que nos permite mantener un control preciso sobre los elementos de nuestro proyecto, como el código fuente, los documentos de diseño y los activos digitales. Esto garantiza que todos los miembros del equipo estén trabajando con la misma versión de los archivos y facilita la colaboración entre desarrolladores, diseñadores y otros profesionales involucrados en el proyecto.

### 6.1.1. Software Development Environment Configuration.

- #### Project Management:

  - ### Trello:
    Una aplicación de gestión de proyectos que facilita el seguimiento de las tareas individuales de cada miembro del equipo de manera sencilla. <br>
    [Link De Registro o Inicio De Sesión](https://trello.com/es)<br>
    Imagen para mostrar evidencia de uso:
    ![trello-image-grupo](assets/img/project-management-trello.png)
    - ### Microsoft Teams
      una plataforma unificada de comunicación y colaboración que combina chat persistente en el lugar de trabajo, reuniones de video, almacenamiento de archivos e integración de aplicaciones. <br>
      [Link De Registro o Inicio De Sesión](https://www.microsoft.com/es-pe/)
      Imagen para mostrar evidencia de uso:
      ![microsoft-teams-image-userpersona](assets/img/evidencia-microsoft-teams.png)

- #### Requirement Management:
  - ### Miro:
    Un sistema que ofrece una amplia gama de plantillas diseñadas para abordar diversos aspectos en la creación y gestión de proyectos. <br>
    [Link De Registro o Inicio De Sesión](https://miro.com/es/login/)
    Imagen para mostrar evidencia de uso:
    ![Miro-image-userpersona](assets/img/evidencia-miro.png)
  - ### UXPressia:
    Es una herramienta en línea que simplifica el proceso de mapeo y comprensión de las necesidades del cliente en un proyecto determinado. <br>
    [Link De Registro o Inicio De Sesión](https://uxpressia.com)
    Imagen para mostrar evidencia de uso:
    ![uxpressia-image-userpersona](assets/img/evidencia-uxpressia.png)
  - ### Structurizr:
    Se trata de una suite de herramientas que posibilita la creación colaborativa de modelos C4 para representar de forma gráfica nuestros productos. <br>
    [Link De Registro o Inicio De Sesión](https://structurizr.com)
- #### Product UX/UI Design:
  - ### Figma:
    Una herramienta de colaboración que facilita el desarrollo conjunto de wireframes y mockups. <br>
    [Link De Registro, Inicio De Sesión y Descarga](https://www.figma.com/downloads/)
  - ### LucidChart:
    Una herramienta colaborativa que posibilita la creación conjunta de wireframes flow y mockups flow. <br>
    [Link De Registro o Inicio De Sesión ](https://www.lucidchart.com/pages/es)
    Imagen para mostrar evidencia de uso:
    ![lucidchart-image-userpersona](assets/img/evidencia-lucidchart.png)
- #### Software Development:

  - ### HTML5:
    Es un lenguaje de etiquetado utilizado para crear la estructura a páginas web. Lo utilizamos para incluir componentes como texto, imágenes, enlaces, botones y videos en nuestras páginas web. <br>
    [Información Relacionada](https://www.esic.edu/rethink/tecnologia/html5-que-es-caracteristicas-y-como-funciona-c#:~:text=El%20HTML5%20es%20un%20estándar,%2C%20estilo%20de%20letra%2C%20etc.)
    Imagen para mostrar evidencia de uso:
    ![uxpressia-image-userpersona](assets/img/html-evidencia.png)
  - ### CSS:
    Un lenguaje de diseño gráfico utilizado para dar formato y estilo a la presentación de un documento escrito en HTML. <br>
    [Información Relacionada](https://developer.mozilla.org/es/docs/Web/CSS)
    Imagen para mostrar evidencia de uso:
    ![uxpressia-image-userpersona](assets/img/evidencia-css.png)
  - ### JavaScript:
    Un lenguaje de programación orientado a objetos dinámico que utilizamos para implementar funcionalidades en un documento HTML. <br>
    [Información Relacionada](https://developer.mozilla.org/es/docs/Web/JavaScript)
    Imagen para mostrar evidencia de uso:
    ![uxpressia-image-userpersona](assets/img/evidencia-uxpressia.png)
  - ### WebStorm:
    Un entorno de desarrollo integrado (IDE) que emplearemos para trabajar con JavaScript. <br>
    [Link De Descarga](https://www.jetbrains.com/es-es/webstorm/)
  - ### Rider:
    Un entorno de desarrollo integrado (IDE) que emplearemos para trabajar con C#. <br>
    [Link De Descarga](https://www.jetbrains.com/es-es/rider/)

- #### Software Documentation:
  - ### Github:
    Se trata de una plataforma utilizada para el alojamiento de versiones del código fuente de un proyecto. Es una herramienta ampliamente popular en el trabajo colaborativo de programadores. <br>
    [Link De Descarga](https://desktop.github.com)
    [Link De Registro o Inicio De Sesión](https://github.com/login)
- #### Software Deployment:
  - ### GitHub Pages:
    Una plataforma que posibilita la realización de despliegues simples directamente desde un repositorio de GitHub. <br>

### 6.1.2. Source Code Management.

Landing Page Repository: [Landing Page Repository](https://github.com/los-seniors-v2/LandingPageFlexPal.git)

- #### GitFlow Implementation:

  Para implementar el flujo de trabajo Gitflow utilizando Git como nuestra herramienta de control de versiones, nos basamos en la entrada de blog "A successful Git branching model" de Vincent Driessen. Esta referencia nos permitió establecer las convenciones detalladas que serán aplicadas en nuestro proyecto
  ![gitflow](assets/img/team_collab_ins.png)

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
- ### TYPESCRIPT
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

  - #### PascalCase
    Mayúscula al principio de cada palabra para nombres de clases y métodos.
    ```
    public class MyClass {
        public void ExampleMethod() {
            // Method code
        }
    }
    ```
  - #### camelCase
    Minúscula al principio con mayúsculas para cada palabra subsiguiente para variables y parámetros.
    ```
    public class MyClass {
        public void ExampleMethod(int exampleNumber) {
            string exampleName = "Example";
            // Method code
        }
    }
    ```
    - #### Reasonable line length
      Mantener líneas de código con longitud adecuada para mejorar la legibilidad.
      ```
      public class MyClass {
          public void ExampleMethod() {
              string message = "This is an example message that spans multiple lines " +
                               "to demonstrate how to maintain a reasonable length.";
               Console.WriteLine(message);
        }
      }
      ```
    - #### Clear comments:
      Utilizar comentarios para explicar el propósito del código de manera concisa.
      ```
      public class MyClass {
          // This method performs an addition operation and returns the result.
          public int Add(int a, int b) {
            return a + b;
           }
      }
      ```
  - #### Single responsibility:

    Cada clase o método debe tener una única función bien definida.

    ```
    // Class responsible for handling basic mathematical operations
    public class MathematicalOperations {
        // Method to add two numbers
        public int Add(int a, int b) {
            return a + b;
        }

        // Method to subtract two numbers
        public int Subtract(int a, int b) {
            return a - b;
        }
    }
    ```

### 6.1.4. Software Deployment Configuration.

- Creación Landing Page:<br>

1. Se crea un repositorio remoto en GitHub
   ![creation-of-repository-lp](assets/img/Creacion_repo.png)
2. Agregar a participantes
   ![adding-members-screenshot-lp](assets/img/miembros_repo.png)
3. Habilitamos GitHub Pages en branch "master" y ruta "/(root)"
   ![deploying-repository-in-github-pages-lp](assets/img/Github_pages.png)

- Creación Front End App:<br>

1. Creación de repositorio dentro de nuestra organización:
   ![creation-of-repository-lp](assets/img/creacion-repositorio-frontendapp.png)
2. Agregar a participantes:
   ![adding-members-screenshot-lp](assets/img/miembros_repo.png)

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
            <td colspan="1">64</td>
		</tr>
        <tr>
			<td colspan="1">Sum of Story Points </td>
            <td colspan="1">64</td>
		</tr>
</tbody>
</table>

#### 6.2.1.2.Aspect Leaders and Collaborators.

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
<tr>
        <td>US001</td>
        <td>Ver introducción atractiva</td>
        <td>T001</td>
        <td>Implementar sección hero completa</td>
        <td><strong>Como</strong> visitante de la plataforma, <strong>quiero</strong> ver una sección introductoria concisa sobre Macetech <strong>para</strong> obtener una primera impresión positiva</td>
        <td>6</td>
        <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US002</td>
        <td>Entender el valor principal</td>
        <td>T002</td>
        <td>Implementar sección valor completa</td>
        <td><strong>Como</strong> visitante de la plataforma, <strong>quiero</strong> identificar y comprender la propuesta de valor central <strong>para</strong> saber si es de mi interés</td>
        <td>6</td>
        <td>Fabrizio Sanchez</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US006</td>
        <td>Iniciar sesión desde CTA visible</td>
        <td>T003</td>
        <td>Implementar CTA login completo</td>
        <td><strong>Como</strong> visitante, <strong>quiero</strong> ver un llamado a la acción claro <strong>para</strong> acceder a funcionalidades personalizadas</td>
        <td>5</td>
        <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US003</td>
        <td>Conocer funcionalidades clave</td>
        <td>T004</td>
        <td>Implementar sección features completa</td>
        <td><strong>Como</strong> visitante, <strong>quiero</strong> identificar las principales funcionalidades <strong>para</strong> analizar si el producto es útil en mi situación</td>
        <td>7</td>
        <td>Ruben Mallma</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US004</td>
        <td>Visualizar video producto</td>
        <td>T005</td>
        <td>Implementar reproductor completo</td>
        <td><strong>Como</strong> visitante, <strong>quiero</strong> ver un video demostrativo <strong>para</strong> entender mejor cómo funciona Macetech</td>
        <td>5</td>
        <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US005</td>
        <td>Conocer opciones membresía</td>
        <td>T006</td>
        <td>Implementar sección membresías completa</td>
        <td><strong>Como</strong> visitante, <strong>quiero</strong> ver un apartado de membresías <strong>para</strong> entender beneficios por nivel</td>
        <td>6</td>
        <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US007</td>
        <td>Conocer miembros equipo</td>
        <td>T008</td>
        <td>Implementar sección equipo completo</td>
        <td><strong>Como</strong> visitante, <strong>quiero</strong> conocer quiénes desarrollan Macetech <strong>para</strong> confiar en el proyecto</td>
        <td>5</td>
        <td>Fabrizio Sanchez</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US008</td>
        <td>Contactar equipo</td>
        <td>T009</td>
        <td>Implementar formulario contacto completo</td>
        <td><strong>Como</strong> visitante, <strong>quiero</strong> poder contactar al equipo <strong>para</strong> hacer preguntas o enviar comentarios</td>
        <td>6</td>
        <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US009</td>
        <td>Descargar aplicación móvil</td>
        <td>T007</td>
        <td>Implementar banners descarga completo</td>
        <td><strong>Como</strong> visitante interesado, <strong>quiero</strong> acceder al enlace de descarga <strong>para</strong> instalar la app</td>
        <td>5</td>
        <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US010</td>
        <td>Visualizar info footer</td>
        <td>T010</td>
        <td>Implementar footer completo</td>
        <td><strong>Como</strong> visitante, <strong>quiero</strong> acceder a información útil en el footer <strong>para</strong> facilitar mi navegación</td>
        <td>5</td>
        <td>Ruben Mallma</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>TS011</td>
        <td>Implementar diseño responsivo</td>
        <td>T011</td>
        <td>Asegurar responsividad completa</td>
        <td><strong>Como</strong> developer, <strong>quiero</strong> implementar diseño responsivo <strong>para</strong> que la página se vea bien en cualquier dispositivo</td>
        <td>8</td>
        <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T011.1</td>
        <td>Ajustar puntos de ruptura CSS</td>
        <td>Implementar media queries y ajustar estilos para diferentes tamaños de pantalla.</td>
        <td>4</td>         <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T011.2</td>
        <td>Probar en dispositivos</td>
        <td>Probar la interfaz en emuladores y dispositivos reales (móvil, tablet, desktop).</td>
        <td>4</td>         <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US014</td>
        <td>Registrar cuenta</td>
        <td>T012</td>
        <td>Formulario registro</td>
        <td><strong>Como</strong> usuario nuevo, <strong>quiero</strong> registrar una cuenta <strong>para</strong> acceder a los servicios</td>
        <td>6</td>
        <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T012.1</td>
        <td>Estructura formulario</td>
        <td>Crear la estructura HTML y estilos básicos para el formulario de registro.</td>
        <td>2</td>         <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T012.2</td>
        <td>Implementar validación</td>
        <td>Añadir validaciones de entrada del usuario en el cliente (JavaScript).</td>
        <td>2</td>         <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T012.3</td>
        <td>Integrar con API</td>
        <td>Conectar el formulario con el endpoint de registro del fake API en Beeceptor.</td>
        <td>2</td>         <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US015</td>
        <td>Iniciar sesión</td>
        <td>T013</td>
        <td>Formulario login</td>
        <td><strong>Como</strong> usuario registrado, <strong>quiero</strong> iniciar sesión con mis credenciales <strong>para</strong> acceder a mi cuenta</td>
        <td>5</td>
        <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
     <tr>
        <td></td>         <td></td>         <td>T013.1</td>
        <td>Estructura formulario</td>
        <td>Crear la estructura HTML y estilos básicos para el formulario de inicio de sesión.</td>
        <td>1</td>         <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T013.2</td>
        <td>Implementar validación</td>
        <td>Añadir validaciones de entrada del usuario en el cliente (JavaScript).</td>
        <td>2</td>         <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T013.3</td>
        <td>Integrar con API</td>
        <td>Conectar el formulario con el endpoint de inicio de sesión del fake API en Beeceptor.</td>
        <td>2</td>         <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US038</td>
        <td>Ver parámetros sensores</td>
        <td>T014</td>
        <td>Dashboard sensores</td>
        <td><strong>Como</strong> usuario, <strong>quiero</strong> consultar parámetros de sensor <strong>para</strong> saber si planta necesita atención</td>
        <td>7</td>
        <td>Fabrizio Sanchez</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T014.1</td>
        <td>Obtener datos sensores</td>
        <td>Obtener los datos de los sensores desde el API del fake API en Beeceptor.</td>
        <td>3</td>         <td>Fabrizio Sanchez</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T014.2</td>
        <td>Mostrar datos</td>
        <td>Renderizar los datos de los sensores en el dashboard (tabla o gráfico).</td>
        <td>4</td>         <td>Fabrizio Sanchez</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US037</td>
        <td>Personalizar nombre maceta</td>
        <td>T015</td>
        <td>Editor nombre</td>
        <td><strong>Como</strong> usuario, <strong>quiero</strong> asignar nombre único <strong>para</strong> identificar fácilmente</td>
        <td>5</td>
        <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
     <tr>
        <td></td>         <td></td>         <td>T015.1</td>
        <td>Crear campo entrada</td>
        <td>Añadir un campo de texto para editar el nombre de la maceta.</td>
        <td>2</td>         <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T015.2</td>
        <td>Implementar guardar</td>
        <td>Añadir la funcionalidad para guardar el nuevo nombre via API.</td>
        <td>3</td>         <td>Flavio Trigueros</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US054</td>
        <td>Registrar planta</td>
        <td>T016</td>
        <td>Selector plantas</td>
        <td><strong>Como</strong> usuario, <strong>quiero</strong> asignar planta a maceta <strong>para</strong> recibir recomendaciones</td>
        <td>6</td>
        <td>Ruben Mallma</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T016.1</td>
        <td>Obtener lista plantas</td>
        <td>Obtener la lista de plantas disponibles desde el API.</td>
        <td>3</td>         <td>Ruben Mallma</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T016.2</td>
        <td>Implementar selector</td>
        <td>Crear la interfaz para seleccionar una planta de la lista.</td>
        <td>3</td>         <td>Ruben Mallma</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US063</td>
        <td>Riego manual</td>
        <td>T017</td>
        <td>Botón riego manual</td>
        <td><strong>Como</strong> usuario, <strong>quiero</strong> activar riego inmediato <strong>para</strong> necesidades puntuales</td>
        <td>5</td>
        <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T017.1</td>
        <td>Crear botón</td>
        <td>Añadir el botón para activar el riego manual en la interfaz.</td>
        <td>2</td>         <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T017.2</td>
        <td>Implementar llamada API</td>
        <td>Configurar la llamada al API para enviar la solicitud de riego.</td>
        <td>3</td>         <td>Juan Pescorán</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US060</td>
        <td>Programar riegos</td>
        <td>T018</td>
        <td>Programador riegos</td>
        <td><strong>Como</strong> usuario, <strong>quiero</strong> horarios fijos <strong>para</strong> plantas con necesidades predecibles</td>
        <td>7</td>
        <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T018.1</td>
        <td>Construir UI programación</td>
        <td>Crear los selectores de día y hora para programar riegos.</td>
        <td>3</td>         <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>          <td>T018.2</td>
        <td>Implementar guardar programación</td>
        <td>Añadir la funcionalidad para guardar los horarios programados via API.</td>
        <td>4</td>         <td>Lucio Yen</td>
        <td>Done</td>
    </tr>
    <tr>
        <td>US075</td>
        <td>Recomendaciones riego</td>
        <td>T019</td>
        <td>Panel recomendaciones</td>
        <td><strong>Como</strong> usuario, <strong>quiero</strong> sugerencias ajustadas <strong>para</strong> optimizar consumo de agua</td>
        <td>6</td>
        <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T019.1</td>
        <td>Obtener recomendaciones</td>
        <td>Obtener las recomendaciones de riego desde el fake API en Beeceptor.</td>
        <td>3</td>         <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tr>
        <td></td>         <td></td>         <td>T019.2</td>
        <td>Mostrar recomendaciones</td>
        <td>Mostrar las recomendaciones de manera clara en la interfaz.</td>
        <td>3</td>         <td>Luiggi Paredes</td>
        <td>Done</td>
    </tr>
    <tbody>
</table>

#### 6.2.1.4.Development Evidence for Sprint Review.

En esta sección se explica y presenta los avances en implementación con relación a los productos de la solución según el alcance del Sprint: Landing Page, Web Applications, Web Services.

Primero, se mostrarán los commits más importantes para el Reporte, los cuales muestran el ciclo de vida del proyecto, y toda la información que se usó, usa y usará para el desarrollo del proyecto:

| Repository          | Branch  | Commit ID                                | Commit Message                    | Commit Message Body                        | Commited on (Date) |
| ------------------- | ------- | ---------------------------------------- | --------------------------------- | ------------------------------------------ | ------------------ |
| JuanPescoran/Report | develop | 98783487238973c5dd4a8097197adb2cf70af00a | feat: added content in chapter IV | added content in all sections of chapter04 | 4/9/2024           |
| JuanPescoran/Report | master  | 889cdc0229a96aa9fca4641ebfccccd71f0d7a5a | feat(assets)                      | added img to master branch                 | 4/9/2024           |

A continuación se presentan los commits más importantes para la Landing Page, los cuales muestran todo el contenido visual y funcionalidades implementadas en el Sprint 2:

| Repository                      | Branch                | Commit ID                                | Commit Message                   | Commit Message Body                                                                                                                                 | Commited on (Date) |
| ------------------------------- | --------------------- | ---------------------------------------- | -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| JDu202012207/LandingPageFlexPal | feat-bienvenida       | 563de4f7bde5ef4a20ce639bc4f6bd881d205856 | feat(welcome-container)          | implemented cta in section home, added slogan and banner.                                                                                           | 4/9/2024           |
| Fabrizio0711/LandingPageFlexPal | feature-testimonios   | d3d404bfa4c98d4bd3311d54d2edca3c2b7f6f51 | feat: added testimonials section | added testimonials section with user feedback                                                                                                       | 4/9/2024           |
| JDu202012207/LandingPageFlexPal | feature-header-footer | f8351fb08d1718af912437127ac10d350a6b0d2c | feat(header-footer)              | implemented logo in header and information in footer.                                                                                               | 4/9/2024           |
| JDu202012207/LandingPageFlexPal | feature-contacto      | c8d979e154ceec2e6b7e924b6aa16137199f743d | feat(contact-us)                 | implemented form, description and labels                                                                                                            | 4/9/2024           |
| JuanPescoran/LandingPageFlexPal | feature-contenido     | db8e4a108071eeed824a148623bf34e7785ea982 | feat(assets): added images       | feat(assets): added all information for hero content, about us, subscriptions and other sections Also, added images for banners and everything else | 4/9/2024           |

#### 6.2.1.5.Testing Suite Evidence for Sprint Review.

#### 6.2.1.6.Execution Evidence for Sprint Review.

#### 6.2.1.7.Services Documentation Evidence for Sprint Review.

#### 6.2.1.8.Software Deployment Evidence for Sprint Review.

#### 6.2.1.9.Team Collaboration Insights during Sprint.

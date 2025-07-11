# Capítulo VI: Product Implementation, Validation & Deployment

La implementación, validación y despliegue del producto constituyen fases críticas en el proceso de desarrollo, ya que garantizan que la visión conceptual inicialmente planteada se materialice en una solución funcional, confiable y accesible para los usuarios finales. A través de estas etapas, no solo se concreta el diseño teórico en una aplicación tangible y operativa, sino que también se evalúa su desempeño en condiciones reales, permitiendo identificar posibles deficiencias, corregir errores y optimizar su funcionamiento. Además, este proceso resulta fundamental para verificar la viabilidad técnica del producto, validar las hipótesis del equipo de desarrollo y asegurar que la experiencia del usuario cumpla con los estándares de calidad esperados, fortaleciendo así la propuesta de valor de la solución tecnológica.

## 6.1. Software Configuration Management

Con el propósito de asegurar un ciclo de vida robusto, eficiente y sostenible para el desarrollo de Macetech, hemos adoptado un conjunto integral de herramientas tecnológicas y metodológicas que respaldan cada una de las etapas clave del proyecto. Estas herramientas nos permiten gestionar el proyecto de manera estructurada, especificar los requerimientos de forma precisa y organizada, diseñar interfaces coherentes y responsivas centradas en la experiencia del usuario, y llevar a cabo un desarrollo colaborativo siguiendo buenas prácticas de ingeniería de software.

En esta sección, se detallarán y justificarán las herramientas seleccionadas para cada uno de los componentes de la solución tecnológica. Específicamente, se abordarán las herramientas de gestión y organización del proyecto, las herramientas de diseño, y también las herramientas orientadas al desarrollo de frontend y backend, esenciales para la construcción de la interfaz de usuario y la lógica del servidor respectivamente.

Asimismo, se explicarán las tecnologías empleadas para la implementación y gestión de la base de datos, que aseguran el almacenamiento eficiente, seguro y escalable de la información; y las herramientas utilizadas en el desarrollo de la aplicación embebida (embedded application) que controla el funcionamiento del dispositivo físico. También se presentarán las herramientas adoptadas para la aplicación en el borde (edge application), y la aplicación móvil, y, finalmente, la landing page.

### 6.1.1. Software Development Environment Configuration

A continuación, se presentan y fundamentan las herramientas adoptadas para el desarrollo de Macetech, clasificadas según su función en las distintas áreas del ecosistema tecnológico de la solución: gestión y organización del proyecto, diseño de interfaces, desarrollo frontend y backend, gestión de base de datos, implementación de la aplicación embebida, desarrollo de la aplicación edge, construcción de la aplicación móvil y diseño de la landing page. Cada una de estas herramientas cumple un rol clave en la arquitectura del sistema y contribuye al cumplimiento de los objetivos funcionales y no funcionales del producto. Para las herramientas basadas en SaaS (Software como Servicio), se proporcionará la URL de acceso a sus respectivas páginas web, mientras que para aquellas que requieren instalación local, se indicará la ruta de descarga adecuada.

#### Project Management

Esta sección se enfoca en la planificación estratégica y supervisión operativa del proyecto a lo largo de todo su ciclo de vida, abarcando la coordinación integral del equipo de trabajo, la gestión de tareas individuales y colectivas, así como el seguimiento de las responsabilidades previamente definidas y asignadas, y su presentación y exposición a stakeholders. Con el fin de estructurar de manera eficiente esta gestión, se ha adoptado un enfoque basado en la aplicación de diversos métodos y herramientas de comunicación, coordinación y administración de recursos humanos. Estas prácticas permiten optimizar los flujos de trabajo, garantizar la trazabilidad de las actividades y fomentar la colaboración efectiva entre los distintos miembros del equipo multidisciplinario involucrado en el desarrollo de la solución Macetech.

- **Reuniones de trabajo - Discord**

  Para la coordinación general del equipo de desarrollo, incluyendo tanto al equipo de frontend como al resto de las áreas técnicas y organizativas, utilizamos Discord como nuestra plataforma principal de comunicación. Discord es una herramienta de comunicación en tiempo real diseñada originalmente para comunidades de videojuegos, pero que ha sido ampliamente adoptada por equipos de trabajo técnico debido a su versatilidad, baja latencia en llamadas, interfaz intuitiva y capacidades de organización mediante canales temáticos y roles personalizados. Estas características la convierten en una solución idónea para Macetech, desarrollado por el equipo de SevenSync, al facilitar una comunicación fluida, continua y sin restricciones de tiempo para reuniones técnicas, sesiones de planificación, revisiones de código, discusiones de diseño, resolución de incidencias y coordinación general del proyecto.<br><br>

  En Discord, se establecieron distintos canales organizados por bounded contexts y áreas funcionales del proyecto (frontend, backend, base de datos, IoT/embedded, diseño, testing, etc.), lo cual permitió segmentar las conversaciones y asignar tareas de forma clara y estructurada. Además, se habilitaron canales de texto y voz para distintos tipos de reuniones (diarias, retrospectivas, planificación, diseño), optimizando la colaboración sincrónica y asincrónica del equipo. Se definieron también roles específicos dentro del servidor (como líder técnico, coordinador de diseño, responsable de base de datos), lo cual facilitó la asignación de responsabilidades y el flujo de trabajo colaborativo. Gracias a esta infraestructura comunicacional, se logró mantener una gestión eficiente del proyecto y un seguimiento preciso de las actividades durante todo el ciclo de vida del desarrollo de Macetech.<br><br>

  - Página oficial de Discord: https://discord.com/<br><br>

- **Comunicación sincrónica y asincrónica - WhatsApp**

  Para la gestión de la comunicación sincrónica y asincrónica de todo el equipo de Macetech se emplea WhatsApp como plataforma principal de mensajería instantánea. WhatsApp, con su amplia adopción y soporte multiplataforma (Android, iOS y escritorio), ofrece un canal confiable para el intercambio de mensajes de texto, notas de voz, llamadas de voz y videollamadas, garantizando comunicación continua y cifrada de extremo a extremo entre los miembros del proyecto. Esta elección se fundamenta en la familiaridad del grupo con la interfaz de usuario, la disponibilidad constante en dispositivos móviles y la posibilidad de compartir rápidamente archivos multimedia y documentos, lo que agiliza la resolución de consultas técnicas y la coordinación de actividades diarias.<br><br>

  En esta plataforma, se ha configurado un chat grupal donde participan todos los integrantes del equipo, lo que facilita la difusión de información global, la asignación de tareas y el seguimiento de hitos o incidentes en tiempo real. Paralelamente, cada colaborador cuenta con la capacidad de establecer comunicación directa con el líder del equipo o con compañeros asignados a tareas específicas, posibilitando interacciones más enfocadas y oportunas para resolver dudas puntuales o recibir retroalimentación inmediata. Gracias a la versatilidad de WhatsApp, se logran establecer flujos de comunicación efectivos tanto para discusiones de alto nivel (mediante videoconferencias grupales) como para consultas rápidas (a través de mensajes o audios), fortaleciendo la cohesión del equipo y asegurando una coordinación eficiente del proyecto Macetech.<br><br>

  - Página oficial de WhatsApp: https://www.whatsapp.com/?lang=es_LA<br><br>

- **Sesiones de Brainstorming y colaboración en tiempo real - Excalidraw**

  Para la facilitación de la ideación visual y la colaboración en tiempo real entre todos los miembros del equipo de Macetech, se emplea Excalidraw como plataforma principal de pizarra digital colaborativa. Excalidraw es una herramienta de código abierto y uso gratuito que proporciona un lienzo virtual ilimitado, permitiendo a los participantes esbozar diagramas, flujos de trabajo y prototipos de manera libre y espontánea. Su interfaz minimalista y basada en vectores ofrece herramientas esenciales (líneas, formas, texto y colores básicos) para representar conceptos técnicos, arquitecturas de sistema, procesos de interacción y esquemas de integración de componentes sin necesidad de conocimientos avanzados en software de diseño. Además, Excalidraw garantiza un entorno orientado a la privacidad y seguridad, ya que no requiere registros complejos ni almacena información sensible de manera persistente.<br><br>

  Dentro del proyecto Macetech, Excalidraw se empleó para sesiones de brainstorming y talleres de diseño, en los cuales se definieron tanto la arquitectura general del sistema (frontend, backend, bases de datos, comunicación con módulos embebidos y lógica de la aplicación móvil) como los flujos de usuarios y la interacción entre los distintos bounded contexts de forma rápida, sencilla y directa. De igual modo, se utilizaron sus capacidades de colaboración en tiempo real para la elaboración de diagramas Kanban simplificados, facilitando la asignación y visualización de tareas durante los sprints. Esta metodología visual permitió al equipo desglosar de manera clara y ordenada las actividades asociadas a cada componente, optimizando la comunicación interfuncional y acelerando la toma de decisiones en torno a la estructuración del proyecto.<br><br>

  - Página oficial de Excalidraw: https://excalidraw.com/<br><br>

- **Desarrollo de documentos de participación - Google Docs**

  Google Docs es un procesador de texto basado en la nube que habilita la creación, edición y almacenamiento de documentos en tiempo real, utilizando Google Drive como repositorio central. La plataforma ofrece un conjunto completo de funcionalidades dirigidas a entornos colaborativos y administrativos: edición simultánea con actualización en tiempo real, control de versiones automático con historial, comentarios y sugerencias, herramientas avanzadas de formato de texto y párrafo (estilos, plantillas, numeración y listas), inserción de objetos multimedia (imágenes, tablas, gráficos vinculados) y enlaces externos, además de correctores ortográfico y gramatical, y soporte para trabajo sin conexión mediante sincronización automática. Su arquitectura en la nube garantiza alta disponibilidad, escalabilidad en el almacenamiento y compatibilidad multiplataforma, lo que facilita tanto la accesibilidad remota como la integración con otros servicios de Google.<br><br>

  En el contexto del proyecto Macetech, Google Docs se ha empleado como herramienta principal para la gestión y seguimiento de responsabilidades del equipo, permitiendo asignar y documentar tareas específicas, definir criterios de evaluación basados en la puntualidad de las entregas, la colaboración continua y la calidad de los entregables. Además, Google Docs ha servido como espacio para la redacción rápida de ideas textuales, la elaboración de reportes de incidencias (bugs, fallos de diseño o inconsistencias en el flujo de la aplicación) y la propuesta de cambios significativos en el alcance o la arquitectura, beneficiándose del control de cambios y del historial de versiones para mantener trazabilidad de las modificaciones. Gracias a estas capacidades, el equipo de Macetech ha optimizado la comunicación documental y ha establecido un registro transparente de la evolución de cada actividad hasta la finalización del proyecto.<br><br>

  - Página oficial de Google Docs: https://docs.google.com/document/u/0/<br><br>

- **Presentaciones de alto impacto a stakeholders - Canva**

  Canva es una plataforma de diseño gráfico basada en la nube que facilita la creación de presentaciones de alto impacto orientadas a audiencias técnicas y no técnicas. Su entorno de trabajo proporciona una amplia variedad de plantillas profesionales, elementos visuales (gráficos, diagramas, iconografía) y herramientas de edición colaborativa, permitiendo al equipo de Macetech construir diapositivas coherentes con la identidad visual del proyecto y adaptadas a distintos públicos, como inversionistas, aliados estratégicos y usuarios finales. Además, su capacidad para exportar presentaciones en formatos livianos (PDF, PPTX, vídeo) garantiza una distribución rápida y confiable de los contenidos, optimizando tanto la transferencia de archivos como la visualización en dispositivos con limitaciones de ancho de banda.<br><br>

  En el marco de las entregas parciales y auditorías internas, utilizamos Canva no solo para el diseño de las exposiciones, sino también para grabar vídeos narrados directamente dentro de la plataforma, diapositiva por diapositiva. Esta funcionalidad permite generar presentaciones en formato multimedia que combinan voz, vídeo, animaciones de entrada y salida de elementos gráficos, así como transiciones personalizadas, de manera que la revisión periódica del avance se realiza con rapidez y calidad profesional. Los vídeos generados facilitan la auditoría técnica y la retroalimentación de los stakeholders, ya que integran el contexto visual de la interfaz de usuario, diagramas de arquitectura y métricas de desarrollo en un único recurso descargable junto al documento final de la presentación.<br><br>

  - Página oficial de Canva: https://www.canva.com/<br><br>

- **Gestión del desarrollo del proyecto, de Product Backlog y Sprint Backlogs - Jira Software**

  Jira Software es una plataforma de gestión de proyectos orientada a equipos de desarrollo ágil, que facilita la planificación, seguimiento y control de todas las actividades relacionadas con el ciclo de vida del software. Basada en la metodología Scrum, Jira permite configurar Product Backlogs y Sprint Backlogs de forma granular, definiendo historias de usuario, tareas técnicas y criterios de aceptación para cada funcionalidad o componente del sistema. Gracias a su flexibilidad, es posible parametrizar flujos de trabajo personalizados (workflows) que reflejen el proceso interno de revisión, aprobación y entrega de cada ítem. Además, Jira ofrece mecanismos de gestión de versiones, seguimiento de incidencias y generación de informes de progreso, lo cual garantiza una transparencia total sobre el estado de avance del proyecto y la identificación temprana de desviaciones con respecto a los plazos establecidos.<br><br>

  Dentro de Macetech, hemos configurado tableros Scrum que contienen los Product Backlogs y Sprint Backlogs correspondientes a cada iteración planificada. Cada miembro del equipo recibe asignaciones específicas con fechas límite claras para asegurar el cumplimiento de los objetivos de cada sprint, abarcando tareas de desarrollo de frontend, backend, base de datos, aplicación embebida y aplicación móvil. Los epics, historias de usuario y tareas técnicas se vinculan entre sí para visualizar dependencias y priorizar entregables críticos en cada ciclo de trabajo. A lo largo del sprint, se realizan reuniones diarias (daily stand-ups) y revisiones de sprint (sprint reviews) dentro de Jira, empleando tableros y filtros personalizados para validar el cumplimiento de los criterios de aceptación y detectar bloqueos.<br><br>

  - Página oficial de Jira: https://www.atlassian.com/software/jira

#### Requirement Management

Esta sección se centra en la gestión integral de requisitos mediante el uso de plataformas para las actividades de Needfinding, elaboración y refinamiento de User Personas, análisis sistemático de entrevistas y mapeo de procesos As-Is y To-Be. Estas plataformas facilitan la construcción de arquetipos de usuario y la visualización de sus necesidades y expectativas a través de plantillas interactivas y reportes dinámicos, además de ofrecer un entorno colaborativo de pizarra digital para capturar insights de entrevistas, estructurar flujos de procesos actuales y diseñar estados futuros óptimos, permitiendo la trazabilidad bidireccional de cada requisito desde su identificación hasta su validación, así como la generación de artefactos compartidos que soportan la toma de decisiones basada en datos cualitativos y cuantitativos a lo largo del ciclo de vida del proyecto.

- **Desarrollo de diagramas de Needfinding con el enfoque UX (User Experience) - UXPressia**

  UXPressia es una plataforma especializada en la creación y gestión de artefactos de experiencia de usuario, orientada a la definición profunda de User Personas, Empathy Maps, Journey Maps e Impact Maps. Esta herramienta basada en la nube permite diseñar perfiles de usuarios detallados, describiendo atributos demográficos, comportamentales y motivacionales, lo cual resulta esencial para alinear los requisitos del producto con las necesidades reales de los usuarios finales. Además, UXPressia proporciona plantillas estandarizadas y capacidades de colaboración en tiempo real, garantizando que todo el equipo de Macetech pueda contribuir simultáneamente a la codificación de insights de usuario, la identificación de _pain points_ y la definición de oportunidades de mejora en cada etapa del ciclo de interacción.<br><br>

  En el contexto de Macetech, UXPressia se emplea para construir User Personas basados en investigaciones de mercado y datos de usuario, definiendo segmentos clave con objetivos y comportamientos específicos. A partir de estos perfiles, se generan Empathy Maps que detallan las emociones, pensamientos, acciones y frustraciones de cada segmento, permitiendo priorizar funcionalidades y diseñar flujos de interacción más empáticos. Asimismo, con Journey Maps, se mapean los puntos críticos del recorrido del usuario, desde la adquisición de una planta hasta el monitoreo constante con Macetech, identificando momentos de valor y posibles fricciones en la experiencia. Finalmente, los Impact Maps facilitan la vinculación entre objetivos de negocio y actividades concretas de diseño e implementación, asegurando que todas las decisiones de desarrollo estén justificadas en métricas de impacto. Gracias a la trazabilidad y la interoperabilidad de UXPressia, el equipo multidisciplinario de SevenSync logra un alineamiento exhaustivo entre investigación UX, diseño de producto y desarrollo técnico, cimentando una experiencia de usuario sólida y validada.<br><br>

  - Página oficial de UXPressia: https://uxpressia.com/<br><br>

- **EventStorming, Flows, Canvases y Mapeo As-Is y To-Be - Miro**

  Miro se configura como una plataforma colaborativa basada en un lienzo digital flexible que facilita la visualización y modelado de procesos complejos, integrando funcionalidades avanzadas para la creación de As-Is y To-Be Scenario Maps, así como para la realización de sesiones de EventStorming. Su infraestructura permite trabajar simultáneamente en un espacio infinito, soportando elementos gráficos como sticky notes, diagramas de flujo, plantillas personalizadas y conexiones semánticas entre objetos. Gracias a su compatibilidad con metodologías ágiles y técnicas de modelado de dominios, Miro resulta idóneo para la representación de artefactos de arquitecturas basadas en Bounded Contexts, ya que posibilita la creación de tableros especializados donde se delimita visualmente cada contexto, se establecen fronteras claras de responsabilidad y se documentan relaciones entre servicios, eventos y actores del sistema.<br><br>

  En el marco del desarrollo de Macetech, Miro se emplea para elaborar detallados As-Is Scenario Maps, que describen los flujos actuales de interacción del usuario y del dispositivo, así como To-Be Scenario Maps que muestran la evolución prevista tras la implementación de nuevas funcionalidades. Asimismo, se usó durante el desarrollo del EventStorming. En las sesiones de EventStorming, los participantes generan un mapa de eventos de dominio, identificando comandos, aggregates y resultados relevantes para los distintos módulos identificados. A continuación, estos eventos se agrupan en Bounded Contexts, diferenciando claramente los ámbitos de frontend, backend, base de datos y sistemas embebidos. Con los Flows y Canvases resultantes, se definen diagramas de secuencia y estructuras lógicas que guían la implementación técnica. Además, se realizan sesiones de brainstorming centradas exclusivamente en la profundización de cada Bounded Context, permitiendo asignar responsabilidades específicas y optimizar la cohesión interna.<br><br>

  - Página oficial de Miro: https://miro.com/es/

#### Product UX/UI Design

Esta sección se orienta al diseño UX/UI mediante el aprovechamiento de herramientas especializadas para la definición de Style Guidelines, la creación de wireframes, mockups, wireflows, user flows y prototipos interactivos. En este sentido, usamos plataformas que actuan como eje central para la composición de sistemas de diseño escalables, gestión de bibliotecas de componentes, especificación de tokens de estilo y colaboración en tiempo real entre diseñadores y desarrolladores. También estructuramos diagramas de wireflows y userflows detallados que documentan la navegación y jerarquía de información, garantizando la coherencia entre la estructura de contenido y la experiencia interactiva, así como la iteración continua de prototipos navegables que permiten pruebas de usabilidad y refinamiento basado en métricas cualitativas y cuantitativas durante todo el ciclo de desarrollo.<br><br>

- **UX/UI Design y Prototyping - Figma**

  Figma se emplea como la plataforma principal para el diseño visual y la elaboración de prototipos interactivos en Macetech, abarcando desde la creación de wireframes iniciales hasta mock-ups de alta fidelidad y prototipos navegables. Gracias a su entorno colaborativo en tiempo real, los diseñadores pueden esbozar rápidamente la estructura básica de la interfaz, definiendo la colocación de componentes, jerarquías de contenido y flujos de navegación, y, de manera simultánea, recibir retroalimentación de desarrolladores frontend, backend y diseñadores. Figma soporta la parametrización de componentes reutilizables, lo que permite establecer sistemas de diseño consistentes, fáciles de mantener y escalables a lo largo de todo el proyecto. Asimismo, sus herramientas de prototipado incorporadas facilitan la simulación de interacciones, transiciones y estados dinámicos sin necesidad de codificación, posibilitando ensayos de usabilidad temprana y validación con usuarios reales antes de la implementación.<br><br>

  Además, Figma se utiliza para definir y documentar las Style Guidelines o pautas de estilo de Macetech, garantizando la coherencia visual y la uniformidad de la marca. Dentro de estas guías se especifican tipografías, paletas de colores, reglas de espaciado, estilos de íconos y comportamientos de interacción (por ejemplo, estados de hover, focus y active), de modo que todos los componentes gráficos se alineen con los estándares de accesibilidad y usabilidad. Las librerías de estilos compartidas facilitan la adopción de estas pautas por parte de los desarrolladores frontend y móvil, asegurando que los elementos de interfaz se implementen según las especificaciones establecidas. De esta manera, Figma no solo actúa como una herramienta de diseño, sino también como un repositorio central de la identidad visual de Macetech, promoviendo la colaboración multidisciplinaria y acelerando el ciclo de diseño-implementación.<br><br>

  - Página oficial de Figma: https://figma.com/<br><br>

- **Wireflows y User flows - LucidChart**

  Lucidchart se emplea como herramienta principal para la creación de Wireflows y User Flows en el proyecto Macetech, aprovechando su capacidad para generar diagramas de flujo de alta calidad y su compatibilidad con múltiples tipos de modelado (UML, C4, BPMN, entre otros). A través de Lucidchart, el equipo de diseño y desarrollo puede esbozar de manera estructurada cómo interactúan los usuarios con la interfaz en cada paso del proceso, incorporando componentes visuales de alta fidelidad que permiten visualizar transiciones, estados de pantalla y puntos de decisión dentro de los flujos de interacción. Las plantillas prediseñadas y la biblioteca de formas personalizables facilitan la representación de íconos, botones, campos de entrada y elementos de navegación, garantizando que los Wireflows reflejen con precisión la estructura de las pantallas y que los User Flows documenten de forma detallada las rutas críticas de uso, desde la autenticación hasta las acciones de configuración.<br><br>

  Además, Lucidchart ofrece funcionalidades de colaboración en tiempo real, lo que permite que varios miembros del equipo, diseñadores de UX, desarrolladores de frontend y backend, editen simultáneamente los diagramas, agreguen comentarios y realicen actualizaciones instantáneas sin necesidad de consolidar archivos estáticos. Gracias a las opciones de exportación en formatos SVG, PNG y PDF, así como a la capacidad de insertar enlaces interactivos dentro de los diagramas, Lucidchart se convierte en un repositorio completo de referencia para validar la usabilidad, optimizar rutas de navegación y asegurar que las implementaciones técnicas correspondan fielmente a los diseños planeados.<br><br>

  - Página oficial de Lucidchart: https://lucidchart.com

#### Product Architecture Design

Esta sección se dedica al diseño de la arquitectura de producto a través de la elaboración de artefactos formales que describen la estructura, los componentes y las interacciones de la solución. Se generarán diagramas C4 para representar los niveles de contexto, contenedores, componentes y código, diagramas de clases UML para modelar entidades, atributos y relaciones, y diagramas entidad-relación para definir esquemas de base de datos lógicos y físicos. Adicionalmente, se incluirán diagramas de despliegue para describir la infraestructura de TI, y mapeos de APIs y dependencias de servicios que documentan puntos de integración. Estos artefactos, versionados y trazables, garantizan la coherencia conceptual y técnica, facilitan la comunicación entre equipos multidisciplinarios y soportan la escalabilidad, mantenibilidad y rendimiento óptimo del producto a lo largo de todo su ciclo de vida.

- **Diagramas UML - LucidChart**

  Lucidchart se emplea para la generación de diagramas de clases UML que representan la estructura y relaciones de las entidades dentro de cada Bounded Context de Macetech. Gracias a su soporte nativo para el modelado UML, la herramienta permite definir clases con atributos, métodos y visibilidades, así como establecer relaciones de herencia, asociación, agregación y composición. Cada diagrama de clases refleja los conceptos clave del dominio y muestra cómo interactúan entre sí dentro de un contexto delimitado. La interfaz de arrastrar y soltar de Lucidchart facilita la creación y modificación de estas estructuras, mientras que las bibliotecas de formas UML garantizan el uso de notaciones estándar.<br><br>

  Dentro de SevenSync, se crearon diagramas de clases específicos para cada Bounded Context identificado mediante sesiones de EventStorming y mapeo en Miro. Estos diagramas, disponibles en Lucidchart, se mantienen versionados y accesibles para todo el equipo, facilitando la coherencia entre la arquitectura lógica y la capa de código en cada módulo del sistema.<br><br>

  - Página oficial de Lucidchart: https://lucidchart.com<br><br>

- **Diagramas C4 - Structurizr DSL**

  Structurizr DSL es un lenguaje específico de dominio basado en texto que facilita la creación y el versionado de diagramas C4 (Contexto, Contenedores y Componentes) de manera reproducible y colaborativa. A través de su sintaxis declarativa, permite definir elementos del sistema, como personas, sistemas externos y límites de contexto, en diagramas de Contexto; detallar las containers que componen la arquitectura en diagramas de Contenedores, y desglosar cada contenedor en sus componentes internos en diagramas de Componentes. Structurizr DSL incorpora convenciones para nombrar, etiquetar y ensamblar relaciones, así como la capacidad de generar vistas específicas basadas en filtros de etiquetas, lo que optimiza la trazabilidad de cambios y la comunicación de la arquitectura entre todos los miembros del equipo.

  En el contexto de Macetech, Structurizr DSL se utilizó para documentar exhaustivamente la arquitectura modular del sistema siguiendo el modelo C4. Primero, se definió un diagrama de Contexto que situó a los usuarios frente a Macetech, dejando claro qué sistemas externos interactúan con la solución. A continuación, en el diagrama de Contenedores, se representaron contenedores clave de toda la plataforma. Cada contenedor se etiquetó según su responsabilidad funcional y se describieron sus protocolos de comunicación. Finalmente, se generaron diagramas de Componentes para cada contenedor no trivial, especificando componentes de alto impacto y relevancia. Gracias a Structurizr DSL, estos diagramas se mantienen sincronizados con el repositorio de código, permitiendo actualizar la arquitectura textualmente y regenerar las vistas, lo que garantiza una documentación arquitectónica coherente y actualizada en todo momento.<br><br>

  - Página oficial de Structurizr DSL: https://structurizr.com/dsl<br><br>

- **Diagramas de base de datos - Vertabelo**

  Vertabelo es una herramienta de modelado de datos relacional basada en la nube que permite diseñar, visualizar y versionar esquemas de bases de datos de manera colaborativa y rigurosa. Emplea una interfaz gráfica intuitiva para la creación de entidades, atributos, relaciones (incluyendo claves primarias y foráneas), índices y restricciones, soportando diversos motores de bases de datos (PostgreSQL, MySQL, SQL Server, entre otros). Vertabelo facilita la generación automática de scripts DDL (Data Definition Language) exportables, que aseguran la coherencia entre el modelo lógico y la implementación física. Además, su sistema de versionado integrado permite mantener un historial de cambios detallado, realizar comparaciones entre distintas versiones del modelo y colaborar en tiempo real con diversos miembros del equipo, garantizando trazabilidad y control de modificaciones en el diseño de la base de datos.<br><br>

  En el proyecto Macetech, Vertabelo se utilizó para modelar de forma estructurada las distintas áreas de datos correspondientes a los Bounded Contexts identificados previamente. El equipo pudo generar el script DDL correspondiente, garantizar que los modelos respondieran a los requerimientos de escalabilidad y consultar la documentación embebida para consultas rápidas. Asimismo, el versionado de los modelos permitió comparar iteraciones, revertir cambios en caso de inconsistencias y coordinar revisiones entre desarrolladores backend y especialistas en base de datos, asegurando que la implementación de la capa de almacenamiento de Macetech estuviera alineada con la visión arquitectónica y los criterios de rendimiento definidos.<br><br>

  - Página oficial de Vertabelo: https://vertabelo.com/

#### Software Development

Esta sección contempla la definición estratégica del stack tecnológico y la configuración de los entornos de desarrollo requeridos para la implementación integral de cada uno de los componentes que conforman la solución digital, los cuales incluyen la Landing Page, la aplicación móvil (Mobile App), la aplicación web (Web App), los servicios web (Web Services), la aplicación embebida (Embedded App), la aplicación Edge (Edge App) y los mecanismos de pruebas (Testing). Se establecerán los lineamientos técnicos y operativos que orientarán la selección de frameworks, arquitecturas y metodologías de codificación, con el objetivo de asegurar la coherencia tecnológica, la eficiencia en el desarrollo, la escalabilidad de las soluciones y su alineamiento con los principios de mantenibilidad, seguridad y rendimiento. Asimismo, se garantizará la integración fluida entre los distintos entornos de desarrollo y pruebas, permitiendo una colaboración efectiva entre equipos multidisciplinarios, una gestión eficiente del ciclo de vida del software y una trazabilidad completa desde la codificación inicial hasta el despliegue en producción.<br><br>

- **Lenguajes de etiqueta y estilo - HTML5 & CSS3**

  HTML5 y CSS constituyen las tecnologías fundamentales para la construcción de la Landing Page de Macetech y para la implementación de los aspectos estáticos de las plantillas en la aplicación web. Con HTML5, se define una estructura semántica robusta que facilita tanto la accesibilidad como el SEO. Se emplean etiquetas específicas para organizar el contenido de la Landing Page, asegurando claridad en la jerarquía de información y compatibilidad con estándares modernos de navegadores.<br><br>

  Por su parte, CSS se encarga de la presentación visual y del comportamiento responsivo tanto de la Landing Page como de las plantillas estáticas de la aplicación web. Se aplican sistemas de diseño basados en CSS Grid para garantizar adaptabilidad en múltiples tamaños de pantalla, desde dispositivos móviles hasta pantallas de escritorio. Asimismo, se definen variables CSS para mantener coherencia en la paleta de colores y estilos tipográficos acordes con las Style Guidelines acordadas en Figma, permitiendo cambios globales de forma centralizada. Gracias a esta combinación de HTML5 y CSS, la Landing Page y las plantillas de Macetech presentan un rendimiento óptimo, una experiencia de usuario uniforme y una base sólida para futuras iteraciones de diseño.<br><br>

  - Página de guía de HTML5 de W3C (World Wide Web Consortium): https://dev.w3.org/html5/spec-LC/
  - Página de guía de HTML5 de W3Schools: https://www.w3schools.com/html/
  - Página de guía de CSS3 de Mozilla Developer Network: https://developer.mozilla.org/es/docs/Web/CSS
  - Página de guía de CSS3 de W3Schools: https://www.w3schools.com/css/default.asp<br><br>

- **Herramientas para la programación del Web Application (Front-End) - JavaScript & TypeScript, con Angular Framework**

  JavaScript es un lenguaje de programación interpretado, dinámico y orientado a prototipos, que se ejecuta directamente en el navegador y posibilita la creación de interfaces interactivas y reactivas. Gracias a su capacidad de manipular el Document Object Model (DOM) en tiempo real, JavaScript permite actualizar el contenido de páginas web sin necesidad de recargas completas, gestionar eventos de usuario (clics, desplazamientos) y realizar peticiones asíncronas a APIs. En el contexto de Macetech, JavaScript sirve como base para la lógica de interacción en el frontend, gestionando comportamientos dinámicos y operaciones en tiempo real que mejoran la experiencia del usuario, como validaciones de formularios, animaciones y consumo de servicios REST.<br><br>

  TypeScript es un superset tipado de JavaScript, desarrollado por Microsoft, que incorpora un sistema de tipos estáticos opcionales, clases, interfaces y módulos. Al compilarse a JavaScript estándar, TypeScript añade una capa de verificación en tiempo de compilación que detecta errores de sintaxis y de tipo antes de que el código se ejecute en el navegador, lo cual incrementa la robustez y mantenibilidad. En el desarrollo de Macetech, TypeScript facilita la detección temprana de inconsistencias, permitiendo refactorizaciones más seguras y documentación implícita mediante anotaciones de tipo. Su integración con entornos de desarrollo modernos ofrece autocompletado y refactorización asistida, lo que acelera la productividad del equipo y minimiza errores.<br><br>

  El Framework Angular es una plataforma de desarrollo frontend basada en TypeScript que sigue una arquitectura basada en componentes, inyección de dependencias y un sistema modular. Angular organiza la aplicación en módulos que agrupan componentes, directivas, servicios y pipes de manera coherente, facilitando la escalabilidad y la separación de responsabilidades. Los componentes en Angular encapsulan la lógica de presentación, el estilo y el comportamiento, promoviendo la reutilización y la cohesión. Angular también proporciona un sistema de enrutamiento integrado que permite definir rutas y parámetros. Para la interfaz de usuario, se utiliza Angular Material, una colección de componentes UI que implementa las pautas de Material Design de Google. Angular Material ofrece una amplia variedad de elementos preconstruidos, como botones, barras de navegación, tarjetas, menús desplegables, diálogos y tablas, optimizados para accesibilidad y rendimiento. Al emplear Angular con JavaScript y TypeScript, junto con Angular Material, el equipo de Macetech puede desarrollar un frontend consistente, modular y mantenible, con componentes estandarizados que garantizan coherencia visual, comportamiento uniforme y experiencias de usuario responsivas en múltiples dispositivos.<br><br>

  - Página oficial de Angular: https://angular.dev/
  - Página de documentación oficial de Angular: https://docs.angular.lat/docs
  - Página de guía de JavaScript de Mozilla Developer Network: https://developer.mozilla.org/es/docs/Web/JavaScript
  - Página oficial de TypeScript: https://www.typescriptlang.org/
  - Página de guía de TypeScript de W3Schools: https://www.w3schools.com/typescript/typescript_intro.php
  - Página oficial de Material Design: https://m3.material.io/
  - Página oficial de Angular Material: https://material.angular.dev/<br><br>

- **Herramientas para la programación del Web Services (Back-End) - RESTful API con C# y con ASP .NET Core Framework**

  C# es un lenguaje de programación multiparadigma, desarrollado por Microsoft, que combina características de tipado estático, orientación a objetos y programación funcional. Su sintaxis clara y su compatibilidad con el Common Language Runtime (CLR) permiten compilar código seguro y altamente optimizado para entornos de producción. En el contexto de Macetech, C# se utiliza para implementar la lógica de negocio del backend con precisión y robustez, aprovechando su sistema de tipos para definir modelos de datos estrictos y facilitar la detección temprana de errores durante la compilación. Además, el ecosistema de C# incluye un amplio conjunto de bibliotecas de .NET, lo que permite reutilizar componentes probados para manejo de excepciones, serialización JSON y acceso a servicios externos.<br><br>

  El Framework ASP .NET Core es una plataforma de desarrollo de aplicaciones web de alto rendimiento, multiplataforma y de código abierto, diseñada para construir servicios y aplicaciones modernas en C#. Su arquitectura modular basada en middlewares posibilita configurar canales de procesamiento HTTP de manera granular, gestionando solicitudes de forma eficiente. En Macetech, ASP .NET Core se emplea para hospedar el servidor de API RESTful, gestionando tareas como enrutamiento de endpoints, autenticación y autorización, interacción con la base de datos (mediante Entity Framework Core) y registro estructurado de eventos.<br><br>

  El Diseño de Arquitectura RESTful API se basa en principios de uniformidad, recursos identificables y operaciones basadas en verbos HTTP (GET, POST, PUT, DELETE). Este enfoque promueve una separación clara entre cliente y servidor, fomentando la reutilización y la escalabilidad del sistema. En el caso de Macetech, la API RESTful define múltiples recursos que exponen operaciones CRUD y acciones específicas. Cada endpoint retorna respuestas en formato JSON, incluyendo códigos HTTP adecuados y encabezados para control de caché o paginación. Al adoptar RESTful API con ASP .NET Core y C#, se logra un backend que puede atender solicitudes simultáneas provenientes de la aplicación web, la aplicación móvil y el dispositivo embebido, garantizando coherencia en la representación de datos, facilidad para versionar la API y compatibilidad con estándares de seguridad como JWT (JSON Web Tokens) en la capa de autenticación.<br><br>

  - Página oficial de C#: https://dotnet.microsoft.com/es-es/languages/csharp
  - Página de guía de C# de Microsoft: https://learn.microsoft.com/es-es/dotnet/csharp/
  - Página oficial de ASP.NET Core: https://dotnet.microsoft.com/es-es/apps/aspnet
  - Página de guía de ASP.NET Core de Microsoft: https://learn.microsoft.com/es-es/aspnet/core/introduction-to-aspnet-core?view=aspnetcore-9.0
  - Página de guía de RESTful API de restfulapi.net: https://restfulapi.net/
  - Página de guía de RESTful API con ASP.NET Core de Microsoft: https://dotnet.microsoft.com/en-us/apps/aspnet/apis

- **Herramientas para la programación del Mobile Application - Dart con Flutter Framework**

  Dart es un lenguaje de programación de propósito general, desarrollado por Google, que está optimizado para crear aplicaciones de alto rendimiento en cliente. Con sintaxis moderna, tipado estático opcional y recolección de basura, Dart permite desarrollar código eficiente tanto para compilación anticipada (AOT) como para compilación just-in-time (JIT). Estas características hacen de Dart una opción idónea para aplicaciones móviles, donde la rapidez en el arranque y la fluidez en la interacción son cruciales. Además, su compatibilidad con la arquitectura de Flutter facilita la construcción de interfaces reactivas y la gestión de estado, utilizando un modelo de widgets declarativo que simplifica la creación de componentes reutilizables.<br><br>

  El framework Flutter, también creado por Google, se apoya en Dart para proporcionar un kit de herramientas UI (UI toolkit) que compila de manera nativa tanto en iOS como en Android, asegurando un rendimiento cercano al código nativo. Flutter incluye un motor de renderizado propio, lo que permite dibujar cada elemento de la interfaz, animaciones y transiciones, con control total sobre los píxeles, sin depender de componentes nativos específicos de cada plataforma. Esto resulta en una experiencia visual y de interacción consistente en dispositivos diversos. En el contexto de Macetech, Flutter y Dart se utilizan para desarrollar la aplicación móvil multiplataforma que complementa la funcionalidad del dispositivo IoT y la plataforma web. El equipo ha estructurado la aplicación en módulos claros, separando la capa de presentación, la capa de lógica de negocio y la capa de datos.<br><br>

  - Página oficial de Flutter: https://flutter.dev/
  - Página de guía de Flutter: https://docs.flutter.dev/
  - Página oficial de Dart: https://dart.dev/
  - Página de guía de Dart: https://dart.dev/docs
  - Página de guía y seguimiento para el modelo del Material Design: https://m3.material.io/<br><br>

- **Herramientas para la programación del Embedded Application - C++**

  C++ es un lenguaje de programación de propósito general que combina características de alto nivel (orientación a objetos, abstracción, plantillas genéricas) con un control de bajo nivel sobre recursos de hardware (manejo explícito de memoria, acceso directo a periféricos). Su naturaleza compilada y tipado estático permite generar binarios altamente optimizados para arquitecturas embebidas con recursos limitados, lo que lo convierte en la opción idónea para el desarrollo de firmware en dispositivos IoT. Adicionalmente, la disponibilidad de bibliotecas de C++ específicas para microcontroladores y la compatibilidad con sistemas operativos en tiempo real facilitan la implementación de bucles de control predictibles, gestión de interrupciones y protocolos de comunicación (MQTT).<br><br>

  En el contexto de Macetech, el IoT Embedded Application se implementa en C++ para garantizar un control preciso de los sensores (medición de humedad, temperatura, luminosidad, pH y salinidad), la lógica de riego automático y la comunicación bidireccional con el backend. El firmware se organiza en módulos C++ que encapsulan la inicialización de periféricos, el muestreo periódico de lecturas y el algoritmo de decisión que activa los actuadores de riego según umbrales configurables. Gracias a la capacidad de C++ para manejar interrupciones de hardware y realizar operaciones de alta frecuencia con ciclos de CPU reducidos, se logra un tiempo de respuesta alto.<br><br>

  - Página oficial de C++ : https://isocpp.org/
  - Página de guía de C con programas IoT: https://learn.microsoft.com/en-us/azure/iot/concepts-developer-guide-device<br><br>

- **Entornos de Desarrollo Integrado - Webstorm, Rider, Android Studio, PyCharm, Wokwi y Visual Studio Code**

  Las Entornos de Desarrollo Integrados (IDEs) constituyen herramientas fundamentales para optimizar la productividad y la calidad del código en cada área del proyecto Macetech. En función del lenguaje y la tecnología utilizada, se han seleccionado entornos especializados que ofrecen características avanzadas de análisis estático, depuración, refactorización y soporte de frameworks específicos:<br><br>

  - Android Studio se utiliza para el desarrollo de la aplicación móvil en Dart con Flutter, gracias a su integración nativa con SDKs de Android y emuladores. Android Studio incluye un editor Visual UI para diseñar interfaces de Flutter, un depurador con visualización de la jerarquía de widgets y herramientas de perfilado que miden el rendimiento en tiempo real (CPU, memoria, GPU). Su sistema de gestión de paquetes y el acceso directo al Flutter Inspector permiten inspeccionar y modificar la estructura de la UI sobre la marcha, ajustando propiedades de widgets, temas y estilos con retroalimentación instantánea.<br><br>

  - PyCharm se ha adoptado como el IDE de referencia para el desarrollo en Python, principalmente en el desarrollo de la aplicación edge. PyCharm ofrece inspección de código basada en PEP8, autocompletado inteligente, análisis de dependencias y detección temprana de errores. Su integración con entornos virtuales (venv, Conda) facilita la gestión de librerías, y el depurador permite establecer puntos de interrupción tanto en código local como remoto (SSH), junto con la visualización de variables en tiempo real.<br><br>

  - Rider se ha elegido para el desarrollo del backend con C# y ASP.NET Core, debido a su integración profunda con el ecosistema de .NET. Rider proporciona análisis estático de código C#, refactorizaciones seguras (reorganización de namespaces, renombrado de símbolos, extracción de métodos), así como un depurador avanzado que permite adjuntar el proceso de ASP.NET Core en ejecución, inspeccionar objetos en memoria y analizar llamadas asíncronas.<br><br>

  - Visual Studio Code (VS Code) se configura como alternativa para aquellos miembros del equipo que no dispongan de acceso a WebStorm o Rider, o para el desarrollo en C++ de la aplicación embebida. VS Code soporta extensiones específicas, como C# for Visual Studio Code, C/C++ (Microsoft), Dart & Flutter, Angular Language Service y Prettier, que dotan al editor de capacidades de autocompletado, linting, depuración y tareas de construcción. Su arquitectura ligera y multiplataforma permite a los desarrolladores trabajar en entornos diversos con una configuración unificada.<br><br>

  - WebStorm se emplea como el IDE principal para el desarrollo de JavaScript, TypeScript y el framework Angular. WebStorm ofrece inspecciones inteligentes de código, autocompletado contextual, navegación rápida entre símbolos y soporte nativo para Angular CLI, lo que permite generar componentes y servicios. Asimismo, facilita la configuración de tareas de compilación mediante archivos de configuración integrados. Su depurador integrado permite establecer puntos de interrupción en tiempo real, evaluando expresiones de JavaScript/TypeScript y trazando el flujo de ejecución del frontend, lo que resulta esencial para detectar problemas de rendimiento.<br><br>

  - Wokwi es la plataforma online elegida para la simulación y validación inicial de los circuitos y firmware en los microcontroladores utilizados por Macetech en su aplicación embebida. Con Wokwi podemos cargar esquemáticos de Arduino, ESP32 y otros chips compatibles, emular periféricos (sensores de humedad, temperatura, pH) y observar la ejecución paso a paso del código en un entorno sandbox sin necesidad de hardware físico. Su editor integrado de código, consola serial virtual y capacidad de compartir proyectos mediante URL pública aceleran la colaboración del equipo de firmware y electrónica.<br><br>

  Con esta selección de IDEs, el equipo de Macetech garantiza que cada desarrollador disponga de un entorno adaptado a las necesidades de su área de trabajo, promoviendo un flujo de desarrollo ágil, coherente y alineado con las mejores prácticas de cada tecnología empleada.<br><br>

  - Página oficial de Android Studio: https://developer.android.com/studio?hl=es-419
  - Página oficial de PyCharm: https://www.jetbrains.com/es-es/pycharm/# 
  - Página oficial de Rider: https://www.jetbrains.com/es-es/rider/
  - Página oficial de Visual Studio Code: https://code.visualstudio.com/
  - Página oficial de Webstorm: https://www.jetbrains.com/es-es/webstorm/
  - Página oficial de Wokwi: https://wokwi.com/ 


#### Software Testing

Esta sección aborda la estrategia integral de aseguramiento de la calidad del software a través de la planificación, ejecución y seguimiento de actividades de verificación y validación orientadas a garantizar la funcionalidad, confiabilidad, usabilidad, seguridad y rendimiento de cada componente del sistema. Se establecerá un enfoque estructurado que incluirá pruebas a nivel unitario, de integración, de sistema y de aceptación. Asimismo, se definirá un conjunto de métricas clave, criterios de cobertura y protocolos de gestión de incidencias que permitan medir de manera objetiva el grado de cumplimiento de los requisitos funcionales y no funcionales. La planificación de pruebas estará alineada con el ciclo de vida del desarrollo, integrándose de forma continua en los flujos de trabajo para facilitar la detección temprana de errores, la reducción del retrabajo y la mejora sostenida del producto.

- **Behavior-Driven Development - Cucumber**

  Cucumber es una herramienta de Behavior-Driven Development (BDD) que permite la definición de criterios de aceptación en formato legible tanto para desarrolladores como para stakeholders, utilizando la sintaxis natural de Gherkin. Cada archivo de características (.feature) contiene escenarios estructurados en pasos que describen comportamientos esperados (“Given–When–Then”), facilitando la comunicación entre el equipo técnico y el equipo de producto.<br><br>

  Para la edición y ejecución de pruebas con Cucumber, empleamos Visual Studio Code junto con extensiones específicas. Estas extensiones habilitan resaltado de sintaxis, completado automático de palabras clave Gherkin, generación de definiciones de pasos, ejecución de escenarios directamente desde el editor y depuración de tests paso a paso. Con esta extensión garantizamos que las pruebas de aceptación sean siempre ejecutables, repetibles y estén enlazadas a los requisitos del negocio, permitiendo validar funcionalidades completas desde el nivel de API hasta la capa de presentación de forma integrada.<br><br>

  - Página oficial de Cucumber: https://cucumber.io/
  - Página de guía de Cucumber: https://cucumber.io/docs/cucumber/<br><br>

- **Unit-Testing con C# - XUnit.net**

  xUnit.net es un framework de pruebas unitarias para C# que sigue las mejores prácticas de diseño de tests y está estrechamente integrado con el ecosistema de .NET Core. xUnit utiliza convenciones de nomenclatura que detectan métodos de prueba mediante atributos como [Fact] y [Theory], lo que simplifica la escritura de tests individuales y de pruebas parametrizadas. En la implementación de Macetech, xUnit se emplea para desarrollar pruebas exhaustivas de la lógica de negocio en el backend, cubriendo servicios, controladores y repositorios del API RESTful.<br><br>

  Gracias a la integración con herramientas de inyección de dependencias, es posible aislar componentes mediante mocks o stubs, lo que facilita la verificación de comportamientos en escenarios unitarios sin recurrir a bases de datos reales. Cada proyecto de prueba xUnit se configura con un archivo de proyecto .csproj que define referencias a los proyectos de producción, bibliotecas de aislamiento y adaptadores de test. Con el uso de XUnit, garantizamos la calidad y la confiabilidad de la solución Macetech.<br><br>

  - Página oficial de XUnit: https://xunit.net/
  - Página de guía de XUnit de Microsoft: https://learn.microsoft.com/es-es/dotnet/core/testing/unit-testing-csharp-with-xunit

#### Software Deployment

Esta sección se enfoca en la planificación y ejecución del proceso de despliegue de software, abarcando las herramientas y entornos necesarios para garantizar una transición controlada, segura y eficiente desde el entorno de desarrollo hacia los entornos de prueba, preproducción y producción. El enfoque adoptado permitirá minimizar riesgos asociados al lanzamiento de nuevas versiones, asegurar la reversibilidad ante fallos. Asimismo, se considerarán aspectos clave como la gestión de credenciales, la disponibilidad de infraestructura escalable, el control de acceso por entornos y la sincronización entre servicios interdependientes.

- **Despliegue de la Landing Page - Github Pages**

  GitHub Pages es un servicio de hosting estático que permite publicar sitios web y páginas de documentación directamente desde un repositorio de GitHub. Mediante la creación de una rama específica, se puede automatizar el despliegue de archivos HTML, CSS, JavaScript y activos estáticos cada vez que se realicen cambios en el repositorio. Al no requerir servidores backend ni bases de datos, ofrece una solución de hosting de bajo costo, con SSL/TLS automático y tiempos de despliegue rápidos, ideal para páginas informativas, blogs, documentación de proyectos y, en este caso, la Landing Page de Macetech.<br><br>

  Para la Landing Page de Macetech, cuya implementación se basa en HTML5, CSS y JavaScript, se ha configurado un workflow que compila y verifica el sitio estático al realizar un push en la rama principal. Una vez aprobados los cambios, el contenido se despliega automáticamente en GitHub Pages, asegurando que los usuarios externos accedan a la versión más reciente sin tiempos de inactividad. Además, se aprovechan las capacidades de GitHub Pages para personalizar el dominio, habilitar HTTPS y gestionar versiones históricas del sitio.<br><br>

  - Página oficial de Github Pages: https://pages.github.com/ <br><br>

- **Despliegue de Aplicaciones Móviles - Firebase App Distribution**

  Firebase App Distribution es un servicio de Google diseñado para facilitar la entrega de aplicaciones móviles a probadores internos y externos antes de su publicación en tiendas oficiales. Funciona como una plataforma centralizada que permite subir paquetes compilados (APK para Android e IPA para iOS), gestionar versiones de prueba y distribuirlas a grupos de testers mediante invitaciones por correo electrónico o enlaces únicos. Entre sus ventajas destacan la facilidad para recopilar retroalimentación temprana, identificar errores en condiciones de uso reales y administrar diferentes canales de prueba sin necesidad de depender de procesos de publicación en Google Play Console o App Store Connect.<br><br>

  En el proyecto Macetech, Firebase App Distribution se utiliza para el despliegue de la aplicación móvil desarrollada en Flutter/Dart, permitiendo que los miembros del equipo y los testers seleccionados instalen compilaciones preelaboradas en sus dispositivos físicos (tanto Android como iOS) de manera ágil y segura. Cada nueva versión del APK o IPA se carga automáticamente desde el proceso de integración continua, se etiqueta con un número de versión semántica y se comparte con los probadores a través de la consola de Firebase. Una vez enviada la invitación, los testers pueden instalar la aplicación en sus dispositivos móviles, ejecutar pruebas de funcionalidad, validar flujos críticos y proporcionar feedback directamente en la plataforma.<br><br>

  - Página oficial de Firebase App Distribution: https://firebase.google.com/docs/app-distribution?hl=es-419

#### Software Documentation

Esta sección contempla la elaboración, estructuración y mantenimiento de la documentación técnica y funcional del software, con el propósito de asegurar la comprensión, trazabilidad y reutilización del conocimiento a lo largo de todo el ciclo de vida del proyecto. Se definirá un marco documental que abarque desde la especificación de requisitos, diseño arquitectónico y detalles de implementación, hasta manuales de instalación, configuración, uso, mantenimiento y pruebas, dirigidos tanto a usuarios técnicos como no técnicos. La documentación será generada de forma iterativa y colaborativa, promoviendo su alineación con los avances del desarrollo y su actualización continua frente a cambios en la solución. Asimismo, se priorizará la claridad, consistencia y estandarización del lenguaje técnico utilizado, integrando diagramas, ejemplos de uso, estructuras de datos, flujos de procesos y referencias cruzadas que faciliten su navegación y comprensión.

- **Control de versiones y repositorios - Github**

  GitHub sirve como plataforma centralizada de control de versiones para todo el ecosistema de Macetech, gestionando el repositorio remotos. En cada repositorio se aplica el GitFlow Workflow, que organiza el trabajo en ramas estables (main/master), ramas de desarrollo (develop), ramas de características (feature), ramas de corrección de errores (hotfix) y ramas de liberación (release). Este enfoque estructurado permite coordinar el avance paralelo de múltiples funcionalidades sin comprometer la estabilidad de las versiones en producción. Adicionalmente, se emplean Conventional Commits para escribir commits uniformes y legibles, lo que facilita la generación automática de changelogs y la trazabilidad de los cambios. Para la numeración de versiones, se sigue el Semantic Versioning (SemVer), etiquetando cada liberación con un esquema Major.Minor.Patch.<br><br>

  Con el fin de aislar responsabilidades y optimizar la mantenibilidad, el código fuente de Macetech se organiza en repositorios separados por aplicación y ramas separadas por Bounded Context. Esta separación garantiza que cada equipo trabaje con su respectivo conjunto de dependencias y políticas de acceso específicos, reduciendo el riesgo de conflictos entre módulos. Asimismo, se usa un repositorio separado para el desarrollo de reportes con respecto a la introducción del producto, sus procesos de definición de requisitos y requerimientos, su listado de product backlog, diagramas, estructuras, arquitecturas, y uso del código en el producto.<br><br>

  - Página oficial de Github: https://github.com/
  - Página de guía de Markdown: https://www.markdownguide.org/<br><br>

- **Documentación de Endpoints - Swagger**

  Swagger (OpenAPI) es un estándar para la documentación interactiva de APIs RESTful que permite describir de manera detallada los endpoints, parámetros, esquemas de datos, códigos de respuesta y modelos de autenticación de un servicio web. A través los modelos de especificación, Swagger genera una interfaz web (Swagger UI) que permite a los desarrolladores explorar cada ruta, probar peticiones en tiempo real y validar esquemas de solicitudes y respuestas sin necesidad de implementar clientes adicionales.<br><br>

  En Macetech, Swagger se configura como parte del backend, de modo que con cada compilación de ASP .NET Core se actualiza la documentación de los recursos disponibles. Esto garantiza que los equipos de frontend (Angular), mobile (Flutter) e incluso el firmware embebido (C++) cuenten con una fuente confiable y siempre sincronizada de los contratos de la API. Además, Swagger permite exportar el documento OpenAPI a formatos como JSON o YAML para integrarlo en herramientas de generación de código. Gracias a esta implementación, la colaboración entre los diferentes contextos bounded de Macetech se fortalece: cada equipo puede consultar, probar y consumir los endpoints de forma rápida y sin ambigüedades, reduciendo errores de integración y acelerando los ciclos de desarrollo.<br><br>

  - Página oficial de Swagger: https://swagger.io/

### 6.1.2. Source Code Management

Para garantizar la trazabilidad y la coherencia en el desarrollo de todos los componentes de Macetech, el equipo adoptará una estrategia de gestión de código fuente basada en GitHub. Este entorno centralizado no solo servirá como repositorio único para la Landing Page, los Web Services y las aplicaciones frontend, edge y embedded, sino también como plataforma de colaboración, revisión de cambios y despliegue continuo. Cada repositorio dispondrá de su propia URL, que se detallará en esta sección, y contendrá tanto el código de producción como las pruebas unitarias y de integración/aceptación, garantizando así un ciclo de desarrollo transparente y fácilmente verificable.

Para organizar el flujo de trabajo en Git, se implementará el modelo GitFlow propuesto por Driessen (2010), definiendo ramas específicas para desarrollo (develop), producción (main), nuevas funcionalidades (feature/), preparaciones de lanzamiento (release/) y correcciones críticas (hotfix/). Las convenciones de nombrado para los lanzamientos seguirán las pautas de Semantic Versioning 2.0.0, de modo que cada versión refleje con claridad cambios importantes, características nuevas y correcciones de errores según su impacto semántico (Preston‑Werner, 2013). Asimismo, los mensajes de commit emplearán el estándar Conventional Commits, facilitando la generación automatizada de changelogs y mejorando la legibilidad del historial de cambios (Conventional Commits, 2020).

**Repositorios en GitHub:**

- Organization: https://github.com/SevenSync 

- Report: https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-report 

- Landing Page: https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page 

- Web Application: https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd 
  
- Mobile Application: https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Mobile-Application 

- Back-End Platform: https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-BackEnd 

- Edge Application: https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Edge-Application 
  
- Embedded Application: https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Embedded-Application

- Acceptance Test: https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest

- Architecture as Code Structure: https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-dsl

**Integrantes de la organización**:
En esta sección, se presentarán todos los usuarios que forman parte de la organización de GitHub del proyecto WHAI, junto con sus nombres de usuario correspondientes. El objetivo es evitar confusiones sobre los autores de los commits en GitHub y facilitar la identificación de los colaboradores al revisar y analizar el reporte y el código desarrollado por nuestro equipo.

###### Tabla 23

*Modelo de integrantes del equipo dentro de la página de organización de Github*

|**Nombre de Usuario**|**Imagen de Perfil**|**Nombre del Integrante del Equipo**|
| ----- | ------ | ----- |
| JuanPescoran | <img src="/assets/img/capitulo-4/profiles/Juan-github.PNG" alt="Pescorán Angulo, Juan Fabritzzio">| Pescorán Angulo, Juan Fabritzzio - U20221C936 |
| FlavioTrigueros | <img src="/assets/img/capitulo-4/profiles/Flavio-github.PNG" alt="Trigueros Chumacero, Flavio Eduardo"> | Trigueros Chumacero, Flavio Eduardo - U202210190 |
| AldhaValenzuelaH | <img src="/assets/img/capitulo-4/profiles/Aldhair-github.PNG" alt="Valenzuela Huillcaya, Aldhair Johan Juan"> | Valenzuela Huillcaya, Aldhair Johan Juan - U20201F572 |
| LucioY250 | <img src="/assets/img/capitulo-4/profiles/Lucio-github.PNG" alt="Yen Cerna, Lucio Heli"> | Yen Cerna, Lucio Heli - U202213143 |

**GitFlow Workflow**:


- **GitFlow Implementation:**

  Para implementar el flujo de trabajo Gitflow utilizando Git como nuestra herramienta de control de versiones, nos basamos en la entrada de blog "A successful Git branching model" de Vincent Driessen. Esta referencia nos permitió establecer las convenciones detalladas que serán aplicadas en nuestro proyecto (Driessen, 2010).

  ###### Figura 172

  _Evidencia del uso de Gitflow para el desarrollo en los repositorios de Macetech_

  <img src="/assets/img/capitulo-6/evidence/gitflow-evidence.png" alt="Evidencia de GitFlow">

- **Master o Main branch**

  La rama principal constituye la versión estable y desplegada en producción de nuestro proyecto. En ella reside el código que se encuentra actualmente operativo, garantizando que cualquier commit en esta rama represente una versión lista para producción. Para mantener su integridad, solo se fusionarán cambios procedentes de ramas de “release” o “hotfix” correctamente validadas.

      Notación: main o master

- **Develop branch**

  La rama de desarrollo aglutina todas las nuevas implementaciones y correcciones aprobadas, que serán parte de la siguiente versión. Actúa como un entorno de integración continua donde se integran y prueban de forma colectiva las contribuciones de las distintas “feature branches”. Una vez que la develop branch alcanza la estabilidad requerida, se crea una rama de “release” y, tras las validaciones finales, sus cambios se fusionan de vuelta tanto a main como a develop para sincronizar el historial. <br><br>

      Notación: develop

- **Feature branch**

  Cada nueva característica o mejora se desarrolla de forma aislada en una rama específica, derivada de develop. Esto facilita el trabajo concurrente de varios desarrolladores sin interferir con el código de otros equipos. Al finalizar el desarrollo y las pruebas unitarias de la funcionalidad, la “feature branch” se fusiona de nuevo en develop, aportando la nueva capacidad al conjunto de funcionalidades en preparación para el próximo lanzamiento.<br><br>

      Notación: feature/

      Ejemplo: feature/iam

**Conventional Commits**

Conventional Commits es un estándar para formatear los mensajes de confirmación en Git de manera consistente y semántica. Al aplicar esta convención, cada commit comunica de forma precisa la naturaleza del cambio, lo que facilita la revisión del historial, la generación automática de registros de cambios y la integración con herramientas de automatización de versiones (Conventional Commits, 2020).

La especificación establece un esquema estructurado, compuesto por un encabezado y un cuerpo, que promueve la claridad y uniformidad en los mensajes, de modo que cualquier miembro del equipo pueda entender rápidamente el propósito y alcance de cada cambio.

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
  camelCase: Variables locales, Parámetros de método, Campos privados (sin \_).
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
            <td colspan="1">El sprint 1 concluyó con el desarrollo de la página web de negocio. Los integrantes del equipo finalizaron este producto y comenzaron a preparar el ambiente de desarrollo para los siguientes productos. El profesor observó que el formulario de contacto no debe estar ubicado al final de la página, además, sostenió que se debe contar con i18n para realizar el cambio de lenguaje. 
            </td>
		</tr>
         <tr>
			<td colspan="1">Sprint 1 – 1 Retrospective Summary </td>
            <td colspan="1">Tras completar el primer Sprint, el equipo identificó varios puntos de mejora como la gestión del tiempo y la responsabilidad en el cumplimiento de tareas. Como reflexión, no se cumplió el objetivo debido a que el sprint 1 debió cubrir la página web de negocio y la plataforma web. Sim embargo, por falta de tiempo no se pudo contemplar el desarrollo del segundo producto. El equipo encara este obstáculo con optimismo para cumplir en el siguiente entregable.</td>
		</tr>
         <tr>
			<td colspan="2">Sprint Goal & User Stories </td>
		</tr>
         <tr>
			<td>Sprint 1 Goal</td>
            <td><strong>Nuestro enfoque es</strong> convertir a los visitantes interesados en jardinería y tecnología para el cuidado de plantas en clientes potenciales, mediante el desarrollo y publicación de la primera versión de la página web de negocio de Macetech. Esta página presentará, de forma clara y visualmente atractiva, el valor diferencial de nuestra maceta inteligente: un sistema automatizado de riego combinado con un algoritmo que adapta el cuidado según el tipo de planta, las condiciones ambientales y los hábitos del usuario. Para generar confianza, incluiremos testimonios reales de los primeros testers, junto a un video donde el equipo fundador explica la visión de Macetech y demuestra el funcionamiento del producto.
Asimismo, la página mostrará una comparación accesible entre las funcionalidades estándar —como el monitoreo básico de humedad, alertas de riego y recomendaciones genéricas— y las funcionalidades premium —como sugerencias personalizadas por especie, programación avanzada de riego y acceso al historial inteligente de crecimiento— con el propósito de despertar la curiosidad por futuras suscripciones.
<br>
<strong>Creemos que esto proporciona</strong> validación temprana del atractivo comercial de Macetech, posicionándonos como una solución tecnológica confiable y deseable dentro del ecosistema de jardinería inteligente. También permite evaluar el interés real de usuarios tempranos y orientar los siguientes pasos de producto y marketing con datos objetivos.

<strong>Esto se confirmará</strong> cuando al menos el 40 % de los visitantes interactúe con la sección de funcionamiento inteligente, el tiempo promedio de permanencia supere los 90 segundos, y recibamos al menos 30 mensajes a través del formulario de contacto solicitando más información o demostraciones del producto.
</td>
		</tr>
        <tr>
			<td colspan="1">Sprint 1 Velocity </td>
            <td colspan="1">19</td>
		</tr>
        <tr>
			<td colspan="1">Sum of Story Points </td>
            <td colspan="1">19</td>
		</tr>
</tbody>
</table>

#### 6.2.1.2. Aspects Leaders and Collaborators

La tabla Aspect Leaders and Collaborators es una herramienta de gestión esencial que proporciona una visión clara y concisa de las responsabilidades individuales dentro del equipo en relación con los diversos aspectos del Sprint. Para el equipo SevenSync, un aspecto fundamental que consideramos son los **Bounded Contexts**. Estos nos permiten delimitar claramente las responsabilidades y el alcance de cada módulo o componente del sistema, lo que facilita el desarrollo, la comprensión y el mantenimiento. Para asegurar una coordinación óptima, especialmente en escenarios donde la colaboración cross-team es vital, es esencial tener claridad sobre quién lidera y quién colabora en cada uno de estos contextos o aspectos clave del proyecto. Esta tabla es particularmente útil para fomentar y gestionar la colaboración cross-team, ya que permite identificar rápidamente a los puntos de contacto para cada área, los líderes de cada bounded context y sus respectivos colaboradores.

| Team Member (Last Name, First Name) | GitHub Username | IAM - Leader (L) / Collaborator (C) | Profile and Preferences - Leader (L) / Collaborator (C) | Subscriptions & Payments - Leader (L) / Collaborator (C) | Asset & Resource Management - Leader (L) / Collaborator (C) | Service Design and Planning - Leader (L) / Collaborator (C) | Service Operation and Monitoring - Leader (L) / Collaborator (C) | Data Analytics - Leader (L) / Collaborator (C) |
|---|---|---|---|---|---|---|---|---|
| Mallma, Ruben | RubDaShen | C | L | C | - | - | C | C |
| Paredes, Luiggi | DevLuiggi | - | C | - | L | - | C | - |
| Pescorán, Juan | JuanPescoran | - | - | - | C | C | L | L |
| Sanchez, Fabrizio | Fabrizio0711 | L | - | - | C | C | - | - |
| Trigueros, Flavio | FlavioTrigueros | - |- | L | - | C | - | C |
| Yen, Lucio | LucioY250 | - | - | - | - | L | C | C |
#### 6.2.1.3.Sprint Backlog 1.

En este primer sprint, nos enfocamos en la implementación de las funcionalidades básicas de la Landing Page, incluyendo la estructura general, el diseño visual y la navegación básica, también se ha creado un reporte que muestra el ciclo de vida de todo nuestro proyecto de software. Estas características son fundamentales para establecer las bases de nuestro producto y proporcionar una experiencia de usuario sólida y coherente.
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
    <tbody>
</table>

A continuación el sprint backlog 1 y el Trello donde se repartieron los trabajos:

Sprint Backlog para el Sprint 1: [Ver Anexo X](https://lucioyen1-1743965307909.atlassian.net/jira/software/projects/SPB/list?filter=statusCategory+%3D+Done+AND+statusCategoryChangedDate+%3E%3D+-1w&atlOrigin=eyJpIjoiMGYzM2ZmYmI4MTc1NDZlODgzNjkwYmQ0NDRjZmVjNDUiLCJwIjoiaiJ9)

<img src="/assets/img/capitulo-6/evidence/sprint-backlog-1-macetech.png" alt="Evidencia de Sprint Backlog para sprint 1">

#### 6.2.1.4.Development Evidence for Sprint Review.

En esta sección se explica y presenta los avances en implementación con relación a los productos de la solución según el alcance del Sprint. En esta iteración, se implementó la Landing Page en su totalidad con todas las secciones Hero Section, funcionalidades clave y beneficios, about-the-team, about-the-product, benchmark de membresías, formulario de contacto, acceso a la platforma de descarga, i18n y diseño responsivo. 

Primero, se mostrarán los commits más importantes para el Reporte, los cuales muestran el ciclo de vida del proyecto, y toda la información que se usó, usa y usará para el desarrollo del proyecto:

| Repository | Branch | Commit ID | Commit Message | Commit Message Body | Commited on (Date) |
| ---------- | ------ | --------- | -------------- | ------------------- | ------------------ |
|DevLuiggi/[upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page)|main|a6a5d97|Initial commit|-|09/05/2025|
|DevLuiggi/[upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page)|main|fba81eb|feat: add initial HTML structure for landing page|-|09/05/2025|
|DevLuiggi/[upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page)|main|641c995|feat: add JavaScript functionality for landing page interactions|-|09/05/2025|
|DevLuiggi/[upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page)|main|e352c30|feat: add CSS styles for responsive landing page|-|09/05/2025|
|DevLuiggi/[upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page)|main|e65d1c5|feat: add assets (images, videos, icons) for landing page|-|09/05/2025|

#### 6.2.1.5.Testing Suite Evidence for Sprint Review.
Para realiza las pruebas, se decidió utilizar 'jest' el cual permite correr pruebas con 'npm test' en scripts de javascript. Para este caso, se probó si el formulario de contacto seguía el flujo sin errores. 

| Repository | Branch | Commit ID | Commit Message | Commit Message Body | Commited on (Date) |
| ---------- | ------ | --------- | -------------- | ------------------- | ------------------ |
|LucioY250/[upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-Landing-Page)|develop|b73525f|test: add landing page testing suite|-|08/07/2025|

#### 6.2.1.6.Execution Evidence for Sprint Review.

Para este sprint, se pudo implementar la aplicación y desplegarla a producción cumpliendo con el diseño y los requerimientos de la página web de negocio planteada. A continuación, se visualizan las capturas con las vistas implementadas. 

<img src="/assets/img/capitulo-6/evidence/landing-page-evidence.jpeg" alt="Evidencia Landing page " width="600px">
<img src="/assets/img/capitulo-6/evidence/landing-page-evidence-2.png" alt="Evidencia Landing page " width="600px">
<img src="/assets/img/capitulo-6/evidence/landing-page-evidence-3.png" alt="Evidencia Landing page " width="600px">
<img src="/assets/img/capitulo-6/evidence/landing-page-evidence-4.png" alt="Evidencia Landing page " width="600px">
<img src="/assets/img/capitulo-6/evidence/landing-page-evidence-5.png" alt="Evidencia Landing page " width="600px">
<img src="/assets/img/capitulo-6/evidence/landing-page-evidence-6.png" alt="Evidencia Landing page " width="600px">

Video de demostración: (Ver Anexo X)

#### 6.2.1.7.Services Documentation Evidence for Sprint Review.

En el alcance de este sprint, no se realizó un web service, sin embargo, a modo de simulación de datos, desplegamos una FAKE API en Beeceptor con los siguientes endpoints:
<img src="/assets/img/capitulo-6/evidence/beeceptor-api-evicende.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-1.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-2.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-3.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-4.jpeg" alt="Evidencia Landing page ">
<img src="/assets/img/capitulo-6/evidence/service-fake-5.jpeg" alt="Evidencia Landing page ">

#### 6.2.1.8.Software Deployment Evidence for Sprint Review.

Para realizar el despligue de la landing page, se utilizó la herramienta Github Pages el cuál permite desplegar páginas estáticas de forma sencilla y veloz. Además, proporciona un pipeline de CI/CD que permite desplegar a producción cada vez que se realiza un commit en la rama 'main'.
Landing Page: Ver Anexo X
<img src="/assets/img/capitulo-6/evidence/github-pages-evidence.png" alt="Evidencia Landing page ">

#### 6.2.1.9.Team Collaboration Insights during Sprint.

La colaboración del equipo se llevó a cabo en la organización de SevenSync, el cúal contiene el repositorio de la Landing Page. En este repositorio, se trabajo en la rama 'develop' y 'main'

<img src="/assets/img/capitulo-6/evidence/landing-page-contributors.png" alt="Evidencia Landing page ">

<img src="/assets/img/capitulo-6/evidence/landing-page-commits-evidence.jpeg" alt="Evidencia Landing page ">

Para este producto, solo una persona logró realizar toda la página web de negocio como se demuestra en la imagen. Se llevó a a cabo de esa manera debido a que era la decisión más eficiente. Los demás integrantes se centraron en la documentación del proyecto y la preparación del ambiente de desarrollo para los siguientes productos.

### 6.2.2. Sprint 2

#### 6.2.2.1. Sprint Planning 2
El sprint planning es una reunión en la metodología ágil donde el equipo planifica las actividades del próximo sprint. Define qué trabajo se hará, cuánto tiempo tomará y quién será responsable. El objetivo es establecer un plan claro y alcanzable para el equipo, fomentando la colaboración y asegurando que todos estén alineados en cuanto a objetivos y prioridades.

<table  style="text-align: center;">
    <tbody>
        <tr>
			<td colspan="1">Sprint #</td>
            <td colspan="1"> Sprint 2  </td>
		</tr>
        <tr>
			<td colspan="2">Sprint Planning Background </td>
		</tr>
        <tr>
			<td colspan="1">Date</td>
            <td colspan="1"> 2025-06-18 </td>
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
			<td colspan="1">Sprint 2 – 2 Review Summary </td>
            <td colspan="1">El sprint 2 concluyó con el desarrollo de la plataforma web, servicio web y aplicativo móvil. Los integrantes del equipo finalizaron este producto y comenzaron a preparar el ambiente de desarrollo para los siguientes productos (edge y embedded). El profesor observó que el formulario de contacto no debe estar ubicado al final de la página, además, sostenió que se debe contar con i18n para realizar el cambio de lenguaje.</td>
		</tr>
         <tr>
			<td colspan="1">Sprint 2 – 2 Retrospective Summary </td>
            <td colspan="1">Tras completar el segundo Sprint, el equipo identificó varios puntos de mejora como la gestión del tiempo y la responsabilidad en el cumplimiento de tareas. Como reflexión, no se cumplió el objetivo debido a que el sprint 1 debió cubrir la página web de negocio y la plataforma web. Sim embargo, por falta de tiempo no se pudo contemplar el desarrollo del segundo producto. El equipo encara este obstáculo con optimismo para cumplir en el siguiente entregable. </td>
		</tr>
         <tr>
			<td colspan="2">Sprint Goal & User Stories </td>
		</tr>
         <tr>
			<td>Sprint 2 Goal</td>
            <td><strong>Nuestro enfoque está</strong> en entregar la propuesta de valor central del sistema de jardinería inteligente de SevenSync, mediante la implementación de la aplicación web para configurar los servicios, el servicio web que permite el monitoreo y cuidado automatizado de las plantas, y la aplicación móvil que habilita el acceso remoto.

<strong>Creemos que esto proporciona</strong> una primera experiencia funcional completa al usuario, permitiéndole interactuar con el sistema desde múltiples interfaces, generando confianza en la solución, facilitando la adopción del producto y validando nuestra arquitectura tecnológica.

<strong>Esto se confirma cuando</strong> los usuarios pueden registrar sus plantas y configuraciones desde la app web, el sistema responde a condiciones del entorno a través del servicio web, y la app móvil permite visualizar parámetros y controlar remotamente el riego automático, sin errores críticos detectados en las pruebas de integración y aceptación.
</td>
		</tr>
        <tr>
			<td colspan="1">Sprint 2 Velocity </td>
            <td colspan="1">42</td>
		</tr>
        <tr>
			<td colspan="1">Sum of Story Points </td>
            <td colspan="1">61</td>
		</tr>
</tbody>
</table>

#### 6.2.2.2. Aspects Leaders and Collaborators
La tabla Aspect Leaders and Collaborators es una herramienta de gestión esencial que proporciona una visión clara y concisa de las responsabilidades individuales dentro del equipo en relación con los diversos aspectos del Sprint. Para el equipo SevenSync, un aspecto fundamental que consideramos son los **Bounded Contexts**. Estos nos permiten delimitar claramente las responsabilidades y el alcance de cada módulo o componente del sistema, lo que facilita el desarrollo, la comprensión y el mantenimiento. Para asegurar una coordinación óptima, especialmente en escenarios donde la colaboración cross-team es vital, es esencial tener claridad sobre quién lidera y quién colabora en cada uno de estos contextos o aspectos clave del proyecto. Esta tabla es particularmente útil para fomentar y gestionar la colaboración cross-team, ya que permite identificar rápidamente a los puntos de contacto para cada área, los líderes de cada bounded context y sus respectivos colaboradores.

| Team Member (Last Name, First Name) | GitHub Username | IAM - Leader (L) / Collaborator (C) | Profile and Preferences - Leader (L) / Collaborator (C) | Subscriptions & Payments - Leader (L) / Collaborator (C) | Asset & Resource Management - Leader (L) / Collaborator (C) | Service Design and Planning - Leader (L) / Collaborator (C) | Service Operation and Monitoring - Leader (L) / Collaborator (C) | Data Analytics - Leader (L) / Collaborator (C) |
|---|---|---|---|---|---|---|---|---|
| Mallma, Ruben | RubDaShen | C | L | C | - | - | C | C |
| Paredes, Luiggi | DevLuiggi | - | C | - | L | - | C | - |
| Pescorán, Juan | JuanPescoran | - | - | - | C | C | L | L |
| Sanchez, Fabrizio | Fabrizio0711 | L | - | - | C | C | - | - |
| Trigueros, Flavio | FlavioTrigueros | - |- | L | - | C | - | C |
| Yen, Lucio | LucioY250 | - | - | - | - | L | C | C |

#### 6.2.2.3. Sprint Backlog 2

El sprint backlog 2 abarcó la implemetnación inicial de todos los productos. En este caso se contempló desarrollar la aplicación web, el servicio en la nube, la aplicación, móvil, la aplicación edge y la aplicación embedida. Se tomó en cuenta el orden de implementación según el valor que aportaba.

<img src="/assets/img/capitulo-6/evidence/sprint-backlog-2-macetech.png" alt="Sprint Backlog 2 " width="600px">

#### 6.2.2.4. Development Evidence for Sprint Review

En esta sección, se documentarán las evidencias de desarrollo más importantes por producto. Para el desarrollo, cada producto se aloja en su propio repositorio.


| Repository | Branch | Commit ID | Commit Message | Commit Message Body | Commited on (Date) |
| ---------- | ------ | --------- | -------------- | ------------------- |------------------ |
| DevLuiggi/[upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd) | develop | 4e32efe | feat(pot-details): add features: recommendations, history and alerts | - | 15/07/2025 |
| LucioY250/[upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd) | develop | 889d5f6 | feat: add plant-catalog component implementation | - | 14/07/2025 |
| Fasz0711/[upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd) | develop | 24c8503 | feat: add membership and payment routes | - | 22/05/2025 |
| DevLuiggi/[upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd) | develop-pots | f76c05b | feat(pots): add pots and route | - | 30/05/2025 |
| Fasz0711/[upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd) | develop-feat-memberships | 24c8503 | feat: add membership and payment routes | - | 22/05/2025 |
| RubDaShen/[upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd) | develop | b0710cc | feat: Add or update the Azure App Service build and deployment workflow config | - | 16/05/2025 |
| Fasz0711/[upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-FrontEnd) | develop-feat-login-register | ed2d780 | feat: routing and global styles; implement login and register components | - | 14/05/2025 |


#### 6.2.2.5. Testing Suite Evidence for Sprint Review

Se desarrollaron archivos .feature en formato gherkin para especificar el comportamiento de nuestras user stories.

| Repository | Branch | Commit ID | Commit Message | Commit Message Body | Commited on (Date) |
| ---------- | ------ | --------- | -------------- | ------------------- | ------------------ |
| Fasz0711/[upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest) | main | 6a6bd51 | Add feature files for managing macetas via Bluetooth, UUID, and web interface | - | 8/07/2025 |
| Fasz0711/[upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest) | main | 4021a24 | Add feature files for subscription management scenarios in web and mobile applications| - | 8/07/2025 |
| Fasz0711/[upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest) | main | 5db13aa | Add feature files for user data management in web and mobile applications | - | 8/07/2025 |

#### 6.2.2.6. Execution Evidence for Sprint Review
Para el alcance de este sprint se desarrollaron las vistas principales de la aplicación web y móvil.

En la aplicación web se contempló el desarrollo del IAM, la vista de perfil, la págian principal donde está la interfaz de macetas y la interfaz de cada maceta. 

<img src="/assets/img/capitulo-6/evidence/web-evidence-1.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-evidence-2.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-evidence-3.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-evidence-4.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-evidence-5.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-evidence-6.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-evidence-7.png" alt="Web Service Evidence" width="600px">

Para la aplicación móvil se contempló el desarrollo inicial del IAM y la vista de perfil de usuario.

<img src="/assets/img/capitulo-6/evidence/mobile-evidence-1.jpeg" alt="Web Service Evidence" width="400px">
<img src="/assets/img/capitulo-6/evidence/mobile-evidence-2.jpeg" alt="Web Service Evidence" width="400px">
<img src="/assets/img/capitulo-6/evidence/mobile-evidence-3.jpeg" alt="Web Service Evidence" width="400px">
<img src="/assets/img/capitulo-6/evidence/mobile-evidence-4.jpeg" alt="Web Service Evidence" width="400px">

#### 6.2.2.7. Services Documentation Evidence for Sprint Review
El servicio web fue documentado por la dependencia OpenAPI el cuál permite mostrar los endpoints en Swagguer UI. 

<img src="/assets/img/capitulo-6/evidence/web-service-evidence-1.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-service-evidence-2.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-service-evidence-3.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-service-evidence-4.jpeg" alt="Web Service Evidence" width="600px">

#### 6.2.2.8. Software Deployment Evidence for Sprint Review

Se hizo el despliegue del cloud api en azure web service. 
<img src="/assets/img/capitulo-6/evidence/web-service-deploy-1.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-service-deploy-2.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-service-deploy-3.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-service-deploy-4.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-service-deploy-5.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-service-deploy-6.jpeg" alt="Web Service Evidence" width="600px">

En el caso de la aplicación web, se hizo el despliegue en firebase.

<img src="/assets/img/capitulo-6/evidence/web-app-deploy-1.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-app-deploy-2.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-app-deploy-3.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-app-deploy-4.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-app-deploy-5.jpeg" alt="Web Service Evidence" width="600px">

#### 6.2.2.9. Team Collaboration Insights during Sprint

La colaboración del equipo en los produtos se llevó a cabo gracias a la organización del Aspects Leaders and Collaborators. Sin embargo, también delegamos tareas por afinidad y habilidades.

Contribuciones y commits de la aplicación web:

<img src="/assets/img/capitulo-6/evidence/web-app-contributors.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-app-commits.png" alt="Web Service Evidence" width="600px">
Contribuciones y commits del servicio web:
<img src="/assets/img/capitulo-6/evidence/web-service-contributors.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-service-commits.png" alt="Web Service Evidence" width="600px">

Contribuciones y commits de la aplicación móvil:

<img src="/assets/img/capitulo-6/evidence/mobile-app-contributors.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/mobile-app-commits.png" alt="Web Service Evidence" width="600px">

### 6.2.3. Sprint 3

#### 6.2.3.1. Sprint Planning 3
El sprint planning es una reunión en la metodología ágil donde el equipo planifica las actividades del próximo sprint. Define qué trabajo se hará, cuánto tiempo tomará y quién será responsable. El objetivo es establecer un plan claro y alcanzable para el equipo, fomentando la colaboración y asegurando que todos estén alineados en cuanto a objetivos y prioridades.

<table  style="text-align: center;">
    <tbody>
        <tr>
			<td colspan="1">Sprint #</td>
            <td colspan="1"> Sprint 3  </td>
		</tr>
        <tr>
			<td colspan="2">Sprint Planning Background </td>
		</tr>
        <tr>
			<td colspan="1">Date</td>
            <td colspan="1"> 2025-06-18 </td>
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
			<td colspan="1">Sprint 3 – 3 Review Summary </td>
            <td colspan="1">Tras completar el tercer Sprint, el equipo identificó varios puntos de mejora como la gestión del tiempo y la responsabilidad en el cumplimiento de tareas. .</td>
		</tr>
         <tr>
			<td colspan="1">Sprint 3 – 3 Retrospective Summary </td>
            <td colspan="1">El sprint 3 concluyó con el desarrollo de la aplicación edge y embedded. Además, se finalizó el desarrollo de los otros productos.</td>
		</tr>
         <tr>
			<td colspan="2">Sprint Goal & User Stories </td>
		</tr>
         <tr>
			<td>Sprint 3 Goal</td>
            <td><strong>Nuestro enfoque está en </strong> completar la solución integral de Macetech integrando la aplicación embebida y el componente Edge, que permiten la conexión directa entre los sensores físicos y el sistema inteligente de monitoreo y riego automático, además de finalizar los desarrollos pendientes de la app web, servicio web y app móvil.

<strong>Creemos que esto proporciona</strong> la capacidad completa del sistema IoT para operar de manera autónoma y en tiempo real, fortaleciendo la propuesta de valor de Macetech como un sistema inteligente y automatizado de cuidado de plantas, y asegurando que todas las plataformas del ecosistema estén listas para su despliegue.

<strong>Esto se confirma cuando</strong> el dispositivo embebido se comunica correctamente con el servicio web al detectar condiciones ambientales (temperatura, humedad, luz), ejecutando decisiones de riego a través del edge, y se registra una tasa de éxito del 90 % en las pruebas de integración entre hardware y software, junto con la validación del 100 % de los criterios de aceptación funcionales pendientes de los productos anteriores. 
</td>
		</tr>
        <tr>
			<td colspan="1">Sprint 3 Velocity </td>
            <td colspan="1">56</td>
		</tr>
        <tr>
			<td colspan="1">Sum of Story Points </td>
            <td colspan="1">107</td>
		</tr>
</tbody>
</table>

#### 6.2.3.2. Aspects Leaders and Collaborators
La tabla Aspect Leaders and Collaborators es una herramienta de gestión esencial que proporciona una visión clara y concisa de las responsabilidades individuales dentro del equipo en relación con los diversos aspectos del Sprint. Para el equipo SevenSync, un aspecto fundamental que consideramos son los **Bounded Contexts**. Estos nos permiten delimitar claramente las responsabilidades y el alcance de cada módulo o componente del sistema, lo que facilita el desarrollo, la comprensión y el mantenimiento. Para asegurar una coordinación óptima, especialmente en escenarios donde la colaboración cross-team es vital, es esencial tener claridad sobre quién lidera y quién colabora en cada uno de estos contextos o aspectos clave del proyecto. Esta tabla es particularmente útil para fomentar y gestionar la colaboración cross-team, ya que permite identificar rápidamente a los puntos de contacto para cada área, los líderes de cada bounded context y sus respectivos colaboradores.

| Team Member (Last Name, First Name) | GitHub Username | IAM - Leader (L) / Collaborator (C) | Profile and Preferences - Leader (L) / Collaborator (C) | Subscriptions & Payments - Leader (L) / Collaborator (C) | Asset & Resource Management - Leader (L) / Collaborator (C) | Service Design and Planning - Leader (L) / Collaborator (C) | Service Operation and Monitoring - Leader (L) / Collaborator (C) | Data Analytics - Leader (L) / Collaborator (C) |
|---|---|---|---|---|---|---|---|---|
| Mallma, Ruben | RubDaShen | C | L | C | - | - | C | C |
| Paredes, Luiggi | DevLuiggi | - | C | - | L | - | C | - |
| Pescorán, Juan | JuanPescoran | - | - | - | C | C | L | L |
| Sanchez, Fabrizio | Fabrizio0711 | L | - | - | C | C | - | - |
| Trigueros, Flavio | FlavioTrigueros | - |- | L | - | C | - | C |
| Yen, Lucio | LucioY250 | - | - | - | - | L | C | C |

#### 6.2.3.3. Sprint Backlog 3
<img src="/assets/img/capitulo-6/evidence/sprint-backlog-3.png" alt="sprint backlog 3" width="600px">

#### 6.2.3.4. Development Evidence for Sprint Review
<img src="/assets/img/capitulo-6/evidence/web-service-commits.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/web-app-commits.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/edge-commits.png" alt="Web Service Evidence" width="600px">

#### 6.2.3.5. Testing Suite Evidence for Sprint Review

| Repository | Branch | Commit ID | Commit Message | Commit Message Body | Commited on (Date) |
| ---------- | ------ | --------- | -------------- | ------------------- | ------------------ |
| Fasz0711/[upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest) | main | 6a6bd51 | Add feature files for managing macetas via Bluetooth, UUID, and web interface | - | 8/07/2025 |
| Fasz0711/[upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest) | main | 4021a24 | Add feature files for subscription management scenarios in web and mobile applications| - | 8/07/2025 |
| Fasz0711/[upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest](https://github.com/SevenSync/upc-pre-202510-1asi0572-2956-SevenSync-AcceptanceTest) | main | 5db13aa | Add feature files for user data management in web and mobile applications | - | 8/07/2025 |

#### 6.2.3.6. Execution Evidence for Sprint Review

<img src="/assets/img/capitulo-6/evidence/embedded-1.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/embedded-2.jpeg" alt="Web Service Evidence" width="600px">

#### 6.2.3.7. Services Documentation Evidence for Sprint Review

<img src="/assets/img/capitulo-6/evidence/edge-1.jpeg" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/edge-2.jpeg" alt="Web Service Evidence" width="600px">


#### 6.2.3.8. Software Deployment Evidence for Sprint Review

#### 6.2.3.9. Team Collaboration Insights during Sprint

<img src="/assets/img/capitulo-6/evidence/edge-contributors.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/edge-commits.png" alt="Web Service Evidence" width="600px">
<img src="/assets/img/capitulo-6/evidence/embedded-contributos.png" alt="Web Service Evidence" width="600px">

### 6.3. Validation Interviews.

Con el objetivo de validar las funcionalidades, beneficios y nivel de adopción potencial de la solución Macetech, se realizaron entrevistas con personas que representan a nuestros segmentos objetivo. Estas entrevistas permitieron recopilar percepciones reales sobre la utilidad, facilidad de uso y valor percibido de la solución, así como identificar oportunidades de mejora. Las respuestas obtenidas ayudaron a confirmar hipótesis clave del producto y a ajustar el diseño en función de las necesidades y expectativas de los usuarios.

#### 6.3.1. Diseño de Entrevistas.

- **Información general del participante**

  1. Nombre:
  2. Edad:
  3. Ubicación actual con provincia y distrito:
  4. Ocupación:

- **Preguntas para ambos segmentos**

  1. ¿Qué impresión general tuviste de la solución Macetech después de la demostración?
  2. ¿Qué funcionalidades del sistema consideras más útiles para el cuidado diario de tus plantas?
  3. ¿Existe alguna funcionalidad que crees que debería estar incluida y que consideras esencial para ti?
  4. ¿Qué tan intuitiva te pareció la interfaz de usuario en cuanto a navegación y uso de las macetas inteligentes?
  5. ¿Cuánto tiempo estimas que te tomaría familiarizarte completamente con el uso del sistema Macetech?
  6. ¿Qué retos enfrentas actualmente al cuidar o monitorear tus plantas que crees que esta solución podría ayudarte a resolver?
  7. ¿Qué tan útil consideras la funcionalidad de recibir alertas sobre el estado de tus plantas en tiempo real?
  8. ¿Cómo te gustaría recibir notificaciones o alertas relacionadas al cuidado de tus plantas (ej. notificaciones móviles, email, sonidos)?
  9. ¿Qué tan importante te parece la posibilidad de registrar y visualizar el historial de salud de tus plantas?
  10. ¿Estarías dispuesto a recomendar esta solución a otras personas interesadas en el cuidado de plantas? ¿Por qué?

#### 6.3.2. Registro de Entrevistas.

Esta sección documenta las entrevistas realizadas a representantes de nuestros segmentos objetivo, con el propósito de recopilar información directa sobre sus hábitos, necesidades y problemas relacionados con el cuidado de plantas. Se incluyen los perfiles de los entrevistados, las preguntas planteadas y un resumen de sus respuestas más relevantes. Este registro permite tener una visión clara de cómo perciben la solución propuesta y qué aspectos consideran más importantes para su adopción y uso continuo.

**Segmento 1 - Personas apasionadas por el cuidado de plantas:**

- **Entrevista N°1**
- **Entrevista N°2**
- **Entrevista N°3**

**Segmento 2 - Especialistas de Jardinería y Áreas Verdes:**

- **Entrevista N°1**
- **Entrevista N°2**
- **Entrevista N°3**

#### 6.3.3. Evaluaciones según heurísticas.

<center> <b> UX Heuristics & Principles Evaluation </b> </center>
<center> <b> Usability – Inclusive Design – Information Architecture </b> </center>

- **CARRERA:** Ingeniería de Software
- **CURSO:** Desarrollo de Soluciones IOT
- **SECCIÓN:** 2956
- **PROFESORES:** Angel Augusto Velasquez Nuñez
- **AUDITOR:** CodeMinds
- **CLIENTE:** SevenSync
- **SITE o APP A EVALUAR:** MaceTech

---

##### TAREAS A EVALUAR

El alcance de esta evaluación incluye la revisión de la usabilidad de las siguientes tareas:

1. Configuración de la cuenta
2. Gestión de notificaciones
3. Gestión de membresía
4. Eliminación de cuenta
5. Cambio de contraseña
6. Visualización de notificaciones de riego, ambiente y sistema.
7. Diferenciación entre notificaciones leídas y no leídas.
8. Uso del botón "Ver Planta" para acceder a más detalles.
9. Aplicación de filtros por categoría en la bandeja de notificaciones.
10. Acción de marcar notificaciones como leídas.
11. Visualización de beneficios entre planes de membresía.
12. Selección y actualización de plan premium.
13. Ingreso de datos de pago y proceso de checkout.
14. Confirmación de suscripción exitosa y siguientes pasos.
15. Visualización de estado general de las macetas.
16. Acceso al detalle de cada planta y sus métricas.
17. Interpretación de valores y recomendaciones.
18. Revisión de historial de sensores, alertas y reportes semanales.

---

##### ESCALA DE SEVERIDAD

Los errores serán puntuados tomando en cuenta la siguiente escala de severidad:

| **Nivel** | **Descripción**                                                                                                                                                     |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1**     | Problema superficial: puede ser fácilmente superado o hasta ignorado por el usuario o ocurre con muy poca frecuencia. No necesita ser arreglado de forma inmediata. |
| **2**     | Problema menor: ocurre con más frecuencia o es más difícil de superar. Prioridad baja para corregirse antes de la siguiente entrega.                                |
| **3**     | Problema mayor: ocurre frecuentemente o es difícil de resolver por los usuarios. Alta prioridad para ser corregido.                                                 |
| **4**     | Problema muy grave: impide el uso de la herramienta. Debe corregirse antes del lanzamiento.                                                                         |

---

##### TABLA RESUMEN

| #   | Problema                                                                              | Escala de severidad | Heurística/Principio violado                                     |
| --- | ------------------------------------------------------------------------------------- | ------------------- | ---------------------------------------------------------------- |
| 1   | El botón “Eliminar cuenta” se encuentra muy cercano al de “Cerrar sesión”             | 3                   | Usabilidad: Prevención de errores                                |
| 2   | El botón “Guardar” en la sección de cambio de contraseña está desactivado por defecto | 2                   | Usabilidad: Visibilidad del estado del sistema                   |
| 3   | Las opciones de configuración de notificaciones no tienen retroalimentación inmediata | 2                   | Usabilidad: Feedback inmediato                                   |
| 4   | En la sección de facturación no está claro qué implica hacer upgrade de plan          | 3                   | Arquitectura de información: Claridad de acciones                |
| 5   | No hay confirmación antes de eliminar la cuenta                                       | 4                   | Usabilidad: Prevención de errores                                |
| 6   | No se muestran iconos distintivos para todas las categorías de notificación           | 2                   | Usability: Visibilidad del estado del sistema                    |
| 7   | No se especifica qué acción realiza el botón "Ver Planta"                             | 2                   | Usability: Correspondencia entre sistema y mundo real            |
| 8   | El filtro de notificaciones "Ambiente" no contiene ejemplos visibles en los mockups   | 1                   | Information Architecture: Is it usable                           |
| 9   | Falta de diferenciación visual entre notificaciones leídas y no leídas                | 3                   | Usability: Visibilidad y control del usuario                     |
| 10  | El plan actual no se distingue visualmente en la tabla comparativa                    | 2                   | Usability: Reconocer en lugar de recordar                        |
| 11  | No hay opción clara para volver atrás desde la vista de precios                       | 2                   | Usability: Control y libertad del usuario                        |
| 12  | El formulario de pago no valida errores en tiempo real                                | 3                   | Usability: Prevención de errores                                 |
| 13  | La confirmación de pago no indica duración ni renovación del plan                     | 2                   | Usability: Visibilidad del estado del sistema                    |
| 14  | La vista general no ordena las macetas según prioridad o alertas                      | 2                   | Usability: Ayuda a los usuarios a reconocer situaciones críticas |
| 15  | No hay acceso directo a modificar datos o nombre de la planta desde la vista general  | 2                   | Usability: Flexibilidad y eficiencia de uso                      |
| 16  | La pestaña de recomendaciones podría pasar desapercibida                              | 1                   | Usability: Visibilidad del estado del sistema                    |
| 17  | Las gráficas de historial carecen de opciones de exportación o visualización ampliada | 2                   | Information Architecture: User control                           |
| 18  | Las alertas no se diferencian suficientemente visualmente en la lista general         | 2                   | Usability: Visibilidad y prevención de errores                   |

---

##### DESCRIPCIÓN DE PROBLEMAS

###### PROBLEMA #1

**Severidad:** 3  
**Heurística violada:** Usabilidad: Prevención de errores  
**Problema:**  
El botón “Eliminar cuenta” está visualmente muy próximo al de “Cerrar sesión”, lo cual puede causar que el usuario lo presione accidentalmente.  
**Recomendación:**  
Separar ambos botones visualmente o añadir un espacio entre ellos para prevenir errores de clic.

---

###### PROBLEMA #2

**Severidad:** 2  
**Heurística violada:** Usabilidad: Visibilidad del estado del sistema  
**Problema:**  
El botón “Guardar” en la sección de cambio de contraseña aparece desactivado incluso cuando se llenan los campos correctamente, generando confusión sobre si hay un error en el ingreso.  
**Recomendación:**  
Habilitar el botón una vez los campos estén correctamente llenos o proporcionar una validación explícita.

---

###### PROBLEMA #3

**Severidad:** 2  
**Heurística violada:** Usabilidad: Feedback inmediato  
**Problema:**  
Las casillas de configuración de notificaciones no muestran una confirmación visual inmediata al ser marcadas o desmarcadas, generando incertidumbre.  
**Recomendación:**  
Añadir mensajes o indicadores de cambio exitoso después de modificar preferencias.

---

###### PROBLEMA #4

**Severidad:** 3  
**Heurística violada:** Arquitectura de Información: Claridad de acciones  
**Problema:**  
El botón de “Actualizar” en la sección de facturación no tiene una descripción clara de qué implica el cambio, ni de los beneficios del nuevo plan.  
**Recomendación:**  
Mostrar información detallada del plan premium antes de que el usuario presione el botón.

---

###### PROBLEMA #5

**Severidad:** 4  
**Heurística violada:** Usabilidad: Prevención de errores  
**Problema:**  
No hay una ventana de confirmación antes de proceder con la eliminación de cuenta, lo que representa un riesgo grave de pérdida de acceso.  
**Recomendación:**  
Añadir un paso intermedio con confirmación explícita y opción de cancelar.

---

###### PROBLEMA #6

- **Severidad:** 2
- **Heurística violada:** Usability: Visibilidad del estado del sistema

**Problema:**  
Algunas notificaciones no incluyen un icono representativo que permita reconocer rápidamente la categoría (riego, ambiente, sistema). Esto reduce la claridad para el usuario al momento de escanear visualmente la información.

**Recomendación:**  
Agregar un ícono para todas las categorías y mantener una codificación visual consistente (color y forma).

---

###### PROBLEMA #7

- **Severidad:** 2
- **Heurística violada:** Usability: Correspondencia entre sistema y mundo real

**Problema:**  
El botón "Ver Planta" no deja claro qué acción concreta se ejecuta: ¿se abre una vista detallada?, ¿se muestra un mapa?, ¿se inicia un riego manual?

**Recomendación:**  
Agregar una breve descripción o tooltip al pasar el cursor, indicando el destino o acción de ese botón.

---

###### PROBLEMA #8

- **Severidad:** 1
- **Heurística violada:** Information Architecture: Is it usable

**Problema:**  
El filtro "Ambiente" aparece en la barra de navegación, pero no se observan notificaciones relacionadas a esa categoría, lo cual genera confusión sobre su utilidad.

**Recomendación:**  
Ocultar filtros vacíos o mostrar un mensaje tipo “No hay notificaciones de esta categoría por el momento”.

---

###### PROBLEMA #9

- **Severidad:** 3
- **Heurística violada:** Usability: Visibilidad y control del usuario

**Problema:**  
No se distingue fácilmente cuáles notificaciones han sido leídas o no. A pesar de que hay un filtro específico, la vista general no incluye una pista visual clara (como un fondo más tenue, borde, o etiqueta).

**Recomendación:**  
Aplicar una diferencia visual explícita entre notificaciones leídas y no leídas para mejorar la navegación y control del usuario.

---

###### **PROBLEMA #10**

**Severidad:** 2  
**Heurística violada:** Usability: Reconocer en lugar de recordar

**Problema:**  
En la tabla comparativa de planes, no se señala claramente cuál es el plan actualmente activo, lo que obliga al usuario a recordar o deducirlo por contexto.

**Recomendación:**  
Agregar una marca visual distintiva (etiqueta, color, ícono) que indique el plan activo en ambas vistas.

**Evidencia visual:**

---

###### **PROBLEMA #11**

**Severidad:** 2  
**Heurística violada:** Usability: Control y libertad del usuario

**Problema:**  
En la vista de precios mensuales, no existe una opción visible para volver o explorar más planes desde la interfaz actual.

**Recomendación:**  
Añadir un botón de navegación para volver a la página anterior o explorar los beneficios de otros planes.

**Evidencia visual:**

---

###### **PROBLEMA #12**

**Severidad:** 3  
**Heurística violada:** Usability: Prevención de errores

**Problema:**  
El formulario de pago permite introducir datos sin mostrar validaciones en tiempo real, lo que podría generar errores frustrantes al final del proceso.

**Recomendación:**  
Implementar validaciones inmediatas para campos como tarjeta, fecha de expiración y CVV, antes de permitir continuar.

**Evidencia visual:**

---

###### **PROBLEMA #13**

**Severidad:** 2  
**Heurística violada:** Usability: Visibilidad del estado del sistema

**Problema:**  
La pantalla de confirmación de pago no indica la duración exacta de la membresía ni cuándo será la próxima renovación.

**Recomendación:**  
Incluir la fecha de finalización del plan y si se renovará automáticamente o requerirá acción por parte del usuario.

---

###### **PROBLEMA #14**

**Severidad:** 2  
**Heurística violada:** Usability: Ayuda a los usuarios a reconocer situaciones críticas

**Problema:**  
La vista principal de macetas no ordena los elementos según niveles de alerta o estado crítico, lo que obliga al usuario a revisar cada planta individualmente.

**Recomendación:**  
Implementar ordenamiento automático o filtros que prioricen las macetas que necesitan acción inmediata (riego, batería, luz).

---

###### **PROBLEMA #15**

**Severidad:** 2  
**Heurística violada:** Usability: Flexibilidad y eficiencia de uso

**Problema:**  
No existe un acceso directo desde la vista general para editar el nombre u otros detalles de la maceta, lo que puede resultar engorroso para usuarios con varias plantas.

**Recomendación:**  
Añadir icono de edición junto al nombre de cada planta o un menú contextual con acciones rápidas.

---

###### **PROBLEMA #16**

**Severidad:** 1  
**Heurística violada:** Usability: Visibilidad del estado del sistema

**Problema:**  
La pestaña de recomendaciones se encuentra oculta por defecto y sugiere contenido importante para el cuidado óptimo de la planta, pero puede pasar desapercibida.

**Recomendación:**  
Resaltar o sugerir proactivamente revisar recomendaciones cuando hay datos fuera del rango óptimo.

---

###### **PROBLEMA #17**

**Severidad:** 2  
**Heurística violada:** Information Architecture: User control

**Problema:**  
El gráfico de historial no cuenta con opciones de exportación, selección de rangos personalizados o zoom, limitando el análisis más profundo.

**Recomendación:**  
Agregar controles de descarga (PDF/CSV), visualización en pantalla completa y rangos personalizables.

---

###### **PROBLEMA #18**

**Severidad:** 2  
**Heurística violada:** Usability: Visibilidad y prevención de errores

**Problema:**  
En la lista principal, las macetas que presentan alertas no se destacan lo suficiente. El ícono de advertencia no resalta frente a otras tarjetas.

**Recomendación:**  
Utilizar colores de fondo o bordes más llamativos para alertas críticas y mostrar un resumen de advertencia al inicio de la pantalla.

## 6.4. Video About-the-Product

https://upcedupe-my.sharepoint.com/:v:/g/personal/u20221c936_upc_edu_pe/EYt5t29wDrRIqEZH6AY51DQBYhJAELOTRAhf5K_BY8VG0w?e=kgwfNZ&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D

<img src="/assets/img/portada/about-the-product.png" alt="Video About The Product">

# Capítulo IV: Solution Software Design

En este capítulo describiremos en detalle el diseño de la solución software de Macetech, trazando desde la arquitectura general hasta los componentes y las interacciones que permiten la gestión inteligente de las macetas. Presentaremos el modelo de capas, incluyendo el servicio de adquisición y procesamiento de datos de los sensores IoT, la capa de negocio para la lógica de riego y análisis de estado de las plantas, y la capa de presentación en la aplicación móvil, así como los patrones de diseño y las tecnologías seleccionadas para garantizar escalabilidad, fiabilidad y seguridad.

Además, se detallarán los flujos de datos, las interfaces de programación (APIs) y los protocolos de comunicación con los dispositivos, junto con las consideraciones de usabilidad y experiencia de usuario que facilitarán un manejo intuitivo y eficiente de Macetech. Por último, se abordarán aspectos claves como la integración con servicios en la nube, el manejo de eventos en tiempo real y las estrategias de despliegue continuo que soportarán la evolución continua de la plataforma.

## 4.1. Strategic-Level Domain-Driven Design.

Strategic Domain-Driven Design, o DDD estratégico es un enfoque arquitectónico que busca alinear la estructura del software con la lógica del negocio y la organización. Este enfoque es esencial para gestionar la complejidad en sistemas grandes y distribuidos, especialmente cuando múltiples equipos trabajan en diferentes partes del sistema.

Según Khononov (2021), el diseño orientado al dominio enfatiza la creación de contextos delimitados ("bounded contexts") que actúan como fronteras explícitas para mantener la coherencia del modelo en cada subdominio, así como el establecimiento de un lenguaje ubicuo ("ubiquitous language") compartido entre los equipos técnicos y los expertos del negocio para asegurar una comunicación precisa y libre de ambigüedades (Khononov, 2021).

Vernon (2016) propone una clara distinción entre dos espacios complementarios: el espacio del problema, dedicado a comprender en profundidad las necesidades y restricciones del negocio, y el espacio de la solución, enfocado en diseñar y aplicar patrones técnicos y arquitectónicos que respondan eficazmente a esos requerimientos. Esta división permite alinear la estrategia empresarial con las decisiones de diseño de software (Vernon, 2016).

Para abordar las decisiones estratégicas en el diseño de software utilizando Domain-Driven Design (DDD), el equipo ha implementado un proceso estructurado que combina técnicas colaborativas y herramientas visuales. Este enfoque facilita la identificación de límites naturales dentro del dominio del negocio, conocidos como Bounded Contexts, y promueve una comprensión compartida entre todos los participantes.

### 4.1.1. EventStorming.

En esta sección se describe el proceso llevado a cabo mediante la técnica de EventStorming para construir una visión compartida del dominio del problema y elaborar una primera versión del modelo del sistema. Siguiendo a Zimarev (2019), EventStorming consiste en un taller colaborativo en el que, a través de la identificación y secuenciación de eventos de negocio, expertos del dominio y miembros del equipo técnico pueden descubrir puntos críticos y dependencias ocultas dentro de procesos complejos (Zimarev, 2019). Además, Tune y Perrin (2024) resaltan cómo esta técnica no solo facilita la generación de requisitos claros, sino que también promueve la alineación socio-técnica al conectar las decisiones de arquitectura con la estrategia organizacional (Tune & Perrin, 2024).

Para ilustrar su alcance, Tune y Perrin definen EventStorming en términos prácticos:

“El EventStorming es un taller dinámico que alinea a los distintos actores, tanto de negocio como técnicos, mediante la identificación de eventos de dominio, permitiendo desentrañar la complejidad del sistema y sentar las bases para un diseño coherente” (Tune & Perrin, 2024).

Como objetivos de la sesión de EventStorming planteamos:

- Reconocer y catalogar los eventos de dominio más significativos, definiendo con precisión su naturaleza y alcance.

- Mapear las dependencias causales y la secuencia temporal entre esos eventos, para visibilizar flujos y puntos de decisión críticos.

- Identificar los procesos de negocio subyacentes, así como los comandos que los activan y los actores responsables de cada acción.

- Generar un insumo estructurado que facilite la posterior delimitación de Bounded Contexts y sirva de base para la definición del modelo de dominio.

**Desarrollo de la sesión**

**Fase 1: Recolección de Eventos de Dominio (Big Picture)**

En esta etapa inicial, todos los participantes plasmaron en notas adhesivas los eventos más relevantes del sistema, redactados en pasado para enfatizar que son hechos consumados dentro del negocio. El objetivo fue generar una “fotografía” global de todos los sucesos críticos, sin filtrar o depurar, de modo que emergiera un panorama amplio de qué ocurre en el dominio.

###### Figura 24

_Primera fase del proceso de EventStorming de Macetech_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-1-collect-domain-events.jpg"></image>

**Fase 2: Refinamiento de Eventos de Dominio**

Con la visión global completada, el equipo realizó una segunda pasada colaborativa para:

- Eliminar duplicados y consolidar sinónimos.

- Aclarar conceptos ambiguos ajustando la redacción de cada evento.

- Ordenar cronológicamente las notas para construir una línea de tiempo coherente.

- Acordar una terminología común que garantizara consistencia semántica.

###### Figura 25

_Segunda fase del proceso de EventStorming de Macetech con la línea de tiempo y refinación de los eventos de dominio_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-2-timeline-and-refine-domain-events.jpg"></image>

###### Figura 26

_Segunda fase del proceso de EventStorming de Macetech con la recolección de eventos de dominio_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-2-1-collect-domain-events.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-2-2-collect-domain-events.jpg.jpg"></image>

**Fase 3: Identificación de disparadores y causas**

A continuación, se analizó cada evento para descubrir qué lo había provocado. Para ello, clasificamos sus orígenes en cuatro categorías principales:

- Acciones de usuario (comandos iniciados desde la interfaz, decisiones de actores).

- Sistemas externos (integraciones o datos entrantes).

- Procesos internos de negocio (temporizadores, condiciones de rutina).

- Reacciones automatizadas (políticas, reglas de negocio que generan eventos secundarios).

De este modo, obtuvimos un mapa de dependencias causales que revela no solo qué sucede, sino por qué y cómo se interconectan los distintos componentes del sistema.

Para esta sección, se necesitará identificar el color de los post-its de Miro para mantener el orden. Se usará esta convención:

###### Figura 27

_Convención de color de post-its utilizados en la tercera fase del proceso de EventStorming de Macetech._

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-summary.jpg"></image>

###### Figura 28

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores._

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes.jpg"></image>

###### Figura 29

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en alertas_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-alerts.jpg"></image>

###### Figura 30

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en la obtención de datos_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-data-ingestion.jpg"></image>

###### Figura 31

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en la Administración de Identidad y Acceso_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-iam.jpg"></image>

###### Figura 32

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en las Notificaciones_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-notifications.jpg"></image>

###### Figura 33

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en la Gestión de Plantas_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-plant-management.jpg"></image>

###### Figura 34

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en la Gestión de Macetas_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-pot-management.jpg"></image>

###### Figura 35

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en las Recomendaciones_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-recommendations.jpg"></image>

###### Figura 36

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en los Reportes_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-reports.jpg"></image>

###### Figura 37

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en las Suscripciones y Membresías_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-subscriptions.jpg"></image>

###### Figura 38

_Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en el Sistema de Riego_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-watering.jpg"></image>

Finalmente, agrupamos los eventos en torno a los agregados del dominio —elementos cohesivos de nuestro modelo— para visualizar:

- Qué comandos disparan cada evento.
- Qué roles o actores están involucrados en esos comandos.
- Qué eventos activan políticas (procesos automáticos) y qué crean modelos de lectura.

Este último paso transforma el Big Picture en un modelo estructurado, orientado a la definición de Bounded Contexts y al diseño detallado de nuestro sistema.

###### Figura 39

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them.jpg"></image>

###### Figura 40

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en las Alertas_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-alerts.jpg"></image>

###### Figura 41

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en el Ingreso de Datos_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-data-ing.jpg"></image>

###### Figura 42

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en la Administración de Identidad y Acceso_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-iam.jpg"></image>

###### Figura 43

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en las Notificaciones_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-notifications.jpg"></image>

###### Figura 44

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en la Gestión de Plantas_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-plant.jpg"></image>

###### Figura 45

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en la Gestión de Macetas_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-pot.jpg"></image>

###### Figura 46

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en las Recomendaciones_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-recom.jpg"></image>

###### Figura 47

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en los Reportes_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-reports.jpg"></image>

###### Figura 48

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en las Suscripciones y Membresías_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-subscriptions.jpg"></image>

###### Figura 49

_Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en el Sistema de Riego_

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-watering.jpg"></image>

Mediante el siguiente enlace podrá acceder y explorar en detalle la pizarra de Miro donde se desarrolló el modelo de EventStorming, organizada por fases e ilustrada con una leyenda explicativa que facilita su revisión:

<a href="https://miro.com/app/board/uXjVI7RMpGc=/?share_link_id=692821022758">Pizarra Miro del proceso de EventStorming</a>

#### 4.1.1.1 Candidate Context Discovery

En esta sección, el equipo describe detalladamente el proceso seguido para la sesión de Candidate Context Discovery, partiendo del modelo de dominio previamente construido mediante EventStorming, con el propósito de identificar y delimitar los Bounded Contexts que compondrán la arquitectura de Macetech. Según Khononov (2021), este enfoque estratégico de Domain‑Driven Design (DDD) requiere una combinación de análisis colaborativo y técnicas sistemáticas para aislar fragmentos del dominio que posean coherencia interna y aporten el mayor valor al negocio

Para asegurar una exploración efectiva de los límites contextuales, se combinaron tres técnicas complementarias, tal como recomienda Khononov (2021):

- **Start‑with‑Value:** consiste en identificar primero aquellos subdominios o flujos de negocio cuyo impacto en la propuesta de valor sea más significativo, de modo que las decisiones de acotamiento prioricen las funcionalidades críticas para el usuario y el negocio

- **Start‑with‑Simple:** implica descomponer el proceso principal en un conjunto mínimo de pasos secuenciales, desde el registro de usuario hasta la generación de recomendaciones, lo cual facilita la visualización y evita solapamientos entre candidatos de contexto

- **Look‑for‑Pivotal‑Events:** se centra en detectar aquellos eventos de dominio que representan cambios de estado fundamentales, ya que estos hitos indefectiblemente marcan fronteras naturales entre contextos

La sesión de Candidate Context Discovery, cuya duración no excedió las dos horas, se organizó como un taller interactivo en el que participaron todos los miembros de nuestro equipo de SevenSync, empleando una herramienta colaborativa de EventStorming, Miro. Durante la misma, se capturaron iterativamente pantallazos que documentan la evolución del modelo de eventos, desde la visión inicial hasta la estructuración final de los contextos. Estas imágenes se incorporarán en la sección para evidenciar la progresión metodológica y facilitar la trazabilidad de las decisiones tomadas.

A partir del modelo de dominio generado con EventStorming, el equipo explica y evidencia el proceso realizado para la sesión de Candidate Context Discovery, en la que se busca identificar los Bounded Contexts. Durante la sesión se siguieron estos pasos:

1. **Preparación y definición de alcance**

   Para garantizar una sesión estructurada y productiva, se llevaron a cabo las siguientes actividades previas: <br><br>

   - **Convocatoria y roles de los participantes**

     Se conformó un grupo interdisciplinario bajo la coordinación de SevenSync, integrado por:<br><br>

     - **Desarrolladores backend y frontend**, responsables de la viabilidad técnica.

     - **Documentadores técnicos** con información total sobre el negocio y las convenciones a utilizar.

     - **Diseñadores UX/UI**, encargados de asegurar la coherencia en la experiencia de usuario.<br><br>

   - **Definición de objetivos y alcance**<br><br>

     - **Propósito principal:** Descomponer el dominio de Macetech, desde el registro inicial del usuario hasta la emisión de recomendaciones y reportes personalizados.

     - **Alcance temporal:** Taller de mínimo dos horas y máximo tres horas en la plataforma Miro utilizando la técnica de EventStorming.<br><br>

   - **Herramientas y materiales de trabajo**<br><br>

     - **Lienzo colaborativo en Miro:** para la colocación y organización dinámica de eventos y comandos.

     - **Post‑its codificados por color:** diferenciando eventos de dominio, comandos de acción e integraciones externas.

     - **Marcadores y cámaras:** para anotar aclaraciones y capturar iteraciones de la evolución del modelo.<br><br>

   - **Asignación de responsabilidades**<br><br>

     - **Facilitador:** orientó la dinámica del taller, gestionó los tiempos y promovió la participación activa.

     - **Escritor:** trasladó al lienzo digital las notas y agrupaciones, asegurando la trazabilidad de cada modificación.

     - **Expertos de dominio:** validaron definiciones, aclararon términos y garantizaron la precisión del lenguaje ubicuo.<br><br>

2. **Técnica Start‑with‑Value**<br><br>

   Con el fin de enfocar el análisis en las áreas de mayor impacto, se realizó:<br><br>

   - **Identificación de “valores núcleo”**

     Cada integrante propuso los flujos de negocio que, a su juicio, aportan el mayor valor a usuario y organización:<br><br>

     - Gestión inicial de macetas y parámetros de configuración.

     - Generación de recomendaciones inteligentes para maximizar la tasa de éxito en el cuidado.

     - Monitoreo en tiempo real, evitando pérdidas derivadas de riegos inadecuados.<br><br>

   - **Priorización de eventos**

     Se listaron todos los eventos detectados y se clasificaron según su impacto (alto, medio, bajo). Solo los catalogados como alto impacto se trasladaron a la siguiente etapa, garantizando que la sesión permaneciera centrada en las funciones críticas.<br><br>

3. **Técnica Start‑with‑Simple**

   Para clarificar la secuencia de operaciones esenciales, se procedió a:<br><br>

   - **Modelado visual con post‑its**

     Para garantizar una visualización ordenada y comprensible de todo el proceso, cada uno de los nueve pasos identificados se plasmó en fichas adhesivas (post-its) de un único color por tipo de actividad. Esta uniformidad evitó solapamientos visuales y facilitó la distinción de responsabilidades entre los distintos subdominios. 

   - **Descomposición en pasos mínimos**

     Con el fin de capturar con precisión el flujo de valor, se esbozó la siguiente tabla sencilla que descompone el proceso en sus componentes más básicos, compuesto por:

###### Tabla 13

_Flujo de valor identificado en el proceso de EventStorming de Macetech_

| Paso | Descripción | Artefactos de Dominio / Evento Pivotal  |
| ---- | -----------| ----------------------- |
| 1    | Registro del usuario en la plataforma.                                                                        | Comando: RegisterUser, Evento: UserRegistered                  |
| 2    | Creación de perfil con datos de contacto y preferencias.                                                      | Comando: CreateProfile, Evento: ProfileCreated                 |
| 3    | Autenticación del usuario, incluyendo verificación 2FA.                                                       | Comando: AuthenticateUser, Evento: UserAuthenticated           |
| 4    | Pago de suscripción a Macetech (plan seleccionado).                                                           | Comando: ProcessSubscriptionPayment, Evento: SubscriptionPaid  |
| 5    | Registro y configuración inicial de la maceta (Pot).                                                          | Comando: RegisterPot, Evento: PotRegistered                    |
| 6    | Definición de riego automático y programación de reportes periódicos.                                         | Comando: SelectWatering, Evento: AutomaticWateringProgrammed   |
| 7    | Identificación de la planta asociada a la maceta (catálogo de especies).                                      | Comando: AddNewPlant, Evento: NewPlantAdded                    |
| 8    | Captura de datos de sensores (humedad, temperatura, pH, salinidad) y obtención de contexto climático vía API. | SensorDataCollected + Evento: ExternalClimateDataFetched       |
| 9    | Generación de recomendaciones y notificaciones de alertas.                                                    | Comando: SelectRecommendation, Evento: RecommendationDisplayed |

4.  **Técnica Look‑for‑Pivotal‑Events**

    Con el propósito de delimitar con precisión los contextos, se identificaron eventos de transición. Un evento de transición, según Khononov (2021), no solo marca un cambio de estado significativo, por ejemplo el paso de “usuario anónimo” a “usuario registrado” o de “maceta sin configurar” a “maceta lista para monitoreo”, sino que también permite priorizar de forma rigurosa el modelado y el desarrollo. Al centrarse en aquellos eventos de mayor impacto, el equipo puede determinar con claridad qué áreas requieren atención inmediata y cuáles funcionalidades deben implementarse primero, garantizando así que las decisiones de diseño estén siempre alineadas con los objetivos de negocio y el valor aportado al usuario.

###### Tabla 14

_Lista de transiciones identificadas en el proceso de EventStorming de Macetech_

| Transición                 | Descripción                                                                                                                                |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| UserRegistered             | Un usuario anónimo se convierte en un usuario registrado, creando una cuenta válida en el sistema.                                         |
| UserProfileCreated         | Un usuario sin perfil asocia y configura su perfil con datos de contacto y preferencias personales.                                        |
| UserProfileDeleted         | Un usuario con perfil configurado elimina su perfil, quedando sin datos personales asociados.                                              |
| UserAuthenticated          | Una sesión no iniciada se valida exitosamente, incluyendo la verificación de dos factores (2FA).                                           |
| SubscriptionPaid           | Un usuario con plan inactivo activa su suscripción mediante el pago correspondiente, habilitando acceso a funcionalidades premium.         |
| SubscriptionCancelled      | Un usuario con suscripción activa cancela su plan, desactivando el acceso a servicios asociados.                                           |
| ExternalClimateDataFetched | El sistema integra datos climáticos externos (vía API) según la ubicación del usuario, aportando contexto ambiental a los sensores.        |
| PotRegistered              | Una maceta previamente no asociada se registra y vincula a un usuario, quedando disponible para su gestión.                                |
| PotSelected                | El usuario selecciona una maceta de la lista de macetas registradas, estableciéndola como activa para operaciones.                         |
| PotDeleted                 | El usuario elimina una maceta registrada, desvinculándola completamente de su cuenta.                                                      |
| BluetoothDevicesPaired     | Se establece una conexión Bluetooth entre la maceta y la red del dispositivo, habilitando la comunicación inalámbrica.                     |
| IrrigationConfigured       | Una maceta sin parámetros de riego definidos adquiere reglas y periodicidad de riego configuradas.                                         |
| PlantIdentified            | Se reconoce la especie de la planta en la maceta y se asignan rangos óptimos de riego, temperatura, pH y salinidad.                        |
| PlantRegistered            | Una planta identificada en maceta se vincula formalmente al usuario, completando su registro en el sistema.                                |
| PlantWatered               | Una planta con baja humedad recibe riego, aumentando su nivel de humedad a parámetros saludables.                                          |
| PlantDeleted               | El usuario elimina la asociación de la planta en la maceta, quedando ésta vacía nuevamente.                                                |
| WateringProgrammed         | Un sistema de riego manual se transforma en un programa de riego automático para la planta especificada.                                   |
| NotificationDisplayed      | El sistema muestra una notificación en la bandeja del usuario sobre un evento relevante (alerta, recomendación).                           |
| NotificationChecked        | El usuario marca una notificación como leída, cambiando su estado a “checada” en la bandeja de notificaciones.                             |
| NotificationDeleted        | El usuario elimina una notificación leída, removiéndola de la bandeja de notificaciones.                                                   |
| SensorDataCaptured         | Los sensores recaban datos brutos (humedad, temperatura, pH, salinidad) y los registran para su procesamiento.                             |
| SensorDataDelivered        | Los datos capturados por los sensores se envían al sistema de la aplicación, quedando disponibles para el usuario.                         |
| SensorDataCollected        | Un sensor pasa de no tener datos almacenados a disponer de registros de las métricas capturadas.                                           |
| SensorHistoryDisplayed     | El sistema presenta al usuario el historial de datos de sensores, permitiendo aplicar filtros y explorar tendencias a lo largo del tiempo. |
| RecommendationGenerated    | Con los datos recopilados, el sistema elabora recomendaciones y alertas personalizadas para el usuario.                                    |
| RecommendationDisplayed    | El usuario visualiza en su bandeja de recomendaciones las acciones sugeridas para optimizar el cuidado de su planta.                       |
| ConsentDelivered           | El sistema muestra al usuario los documentos de términos y condiciones, dejando constancia de su presentación.                             |
| ConsentAccepted            | El usuario otorga su consentimiento a los términos y condiciones, registrándose dicha aceptación en el sistema.                            |
| ConsentRejected            | El usuario rechaza los términos y condiciones, registrándose dicha negativa en el sistema.                                                 |

- **Agrupación por afinidad de eventos**

  Sobre el lienzo, los post‑its se reagruparon alrededor de cada evento pivotal, permitiendo visualizar con claridad los límites naturales entre posibles contextos.

**5. Visualización evolutiva**

   Con el objetivo de documentar de manera sistemática el avance del modelo y garantizar su trazabilidad, se implementó un proceso de registro visual en intervalos regulares:
   
   - **Capturas iterativas**

      Para conservar un historial detallado de la evolución del tablero, se generaron capturas de pantalla en Miro a lo largo de toda la sesión de trabajo, siguiendo estos hitos: <br><br>

      - **Estado inicial:** todos los eventos recolectados, aún sin clasificar ni ordenar, reflejando la materia prima del modelado.

      - **Después de Start-with-Value:** se destacaron exclusivamente aquellos eventos con mayor repercusión en la generación de valor, lo que permitió centrar el análisis en los aspectos críticos del dominio.

      - **Después de Start-with-Simple:** se reorganizó el conjunto de eventos siguiendo un criterio cronológico básico, facilitando la comprensión del flujo secuencial de las interacciones.

      - **Después de Look-for-Pivotal-Events:** se identificaron y agruparon los eventos clave que actúan como puntos de inflexión, sentando las bases para la delimitación de subdominios.

      - **Versión final:** se plasmó la consolidación de los candidatos a contextos delimitados, incorporando agregados, políticas y responsabilidades, y validando la coherencia global del modelo.

   * **Registro meticuloso**

      Cada imagen se anotó con fecha, hora y una breve descripción de los ajustes realizados, asegurando que el informe refleje con exactitud la evolución metodológica, y facilitando la inclusión de estas evidencias en la sección correspondiente.

**6. Candidatos a Bounded Context**

A continuación presentamos la sección de Candidatos a Bounded Contexts, donde listamos todos los contextos identificados en la sesión inicial (incluyendo aquellos que finalmente no se consolidaron) y la justificación de su inclusión o exclusión en el conjunto definitivo.

###### Tabla 15

_Lista de candidatos a Bounded Context identificados en el proceso de EventStorming de Macetech_

| Contexto    | Responsabilidades clave    | ¿Pasa al diseño  |
| ---------- | -----------| -------------------- |
| IAM                         | Autenticación (login/logout, manejo de sesiones), emisión y validación de JWT y tokens de refresco, soporte 2FA, gestión de permisos y roles. CRUD de cuentas de usuario, eliminación, recuperación de contraseña, validación de datos de contacto                         | **Consolidado:** La seguridad y control de acceso son requisitos no negociables. Al agrupar login, emisión de tokens y 2FA en un único contexto, se garantiza la consistencia en la gestión de credenciales, la separación de responsabilidades y la escalabilidad de las políticas de acceso. También es el núcleo del ciclo de vida de cuentas de usuario. Centralizar creación, actualización y baja de cuentas asegura trazabilidad de eventos y facilita la auditoría.   |
| Profile and Preferences    | Almacenamiento/actualización de datos de perfil, preferencias del usuario, integración Geo API, y normalización de direcciones del usuario  | **Consolidado:** Ofrece personalización y localización sin contaminar otros contextos dentro de la solución. Al abstraer el manejo de datos de perfil, contacto y preferencias, se optimiza la reutilización de la Geo API y se garantiza que las modificaciones de esquema o validaciones no afecten la lógica de negocio de autenticación ni de facturación. Esto involucra también preferencias de notificaciones, apariencia de la aplicación, etc. |
| Asset & Resource Management | CRUD de macetas, configuración de parámetros de riego (frecuencia, volumen, límites), metadatos (nombre, ID), persistencia histórica de los datos obtenidos | Este componente constituye la base de la capa IoT, ya que permite registrar las macetas junto con sus parámetros iniciales. Centralizar en este punto la configuración posibilita desacoplar la lógica de los sensores de la lógica del resto de la aplicación, lo que a su vez favorece la extensibilidad del sistema. De este modo, se pueden incorporar nuevos tipos de dispositivos sin generar impactos en los módulos de control ni en los procesos analíticos, asegurando una arquitectura más flexible y escalable.  |
| Service Design and Planning | Catálogo de especies de plantas junto con sus rangos óptimos de pH, luminosidad, temperatura y salinidad, así como la validación de la correspondencia planta–maceta. Engloba el diseño y la planificación del servicio y de sus funcionalidades, desde la selección de la especie hasta la configuración de sus parámetros.  | **Consolidado:** Este enfoque posibilita la evolución del modelo botánico de manera autónoma respecto al hardware subyacente. Al aislar la lógica del servicio de las especies y sus rangos óptimos, se facilita la incorporación de nuevas variedades vegetales o la integración de proveedores de datos externos, sin que ello afecte a otras capas. De este modo, se mantiene la robustez y la coherencia arquitectónica del sistema. |
| Subscriptions & Payments    | Definición y gestión de los planes de suscripción, del procesamiento seguro de las transacciones y de la administración integral de las facturas, así como de la integración con pasarelas de pago y webhooks con la API externa de Stripe. De este modo, se garantiza la trazabilidad de los cobros y la coherencia en la facturación..  | **Consolidado:** Este contexto soporta tanto el modelo de negocio freemium como las suscripciones de pago. Al mantener un dominio dedicado exclusivamente a la facturación, se aísla cualquier cambio en las pasarelas de pago, en los planes tarifarios o en los flujos de cobro, evitando impactos en la lógica de usuario o en los sistemas físicos. Esta separación otorga la flexibilidad necesaria para ajustar políticas de precios y métodos de pago con el mínimo esfuerzo y sin fricciones entre módulos.  |
| Service Operation and Monitoring | Agrupa las funciones de verificación de estado (health checks), registro de logs críticos y generación y envío de alertas (push y e-mail), así como la visualización de un dashboard operativo. Además, ejecuta las operaciones de la maceta, incluyendo riego, notificaciones y recomendacionesm y supervisa el estado de la planta mediante la interacción de sensores y actuadores, integrando tanto la aplicación embebida (embedded app) como la de borde (edge app). | **Consolidado:** Este contexto centraliza la supervisión y la gestión de alertas en un único módulo, evitando la fragmentación de la lógica de notificaciones. Al consolidar la detección de fallos y su envío al usuario, se asegura la coherencia en los umbrales y en los canales de comunicación, además de facilitar la medición y optimización del uptime. Este componente constituye el núcleo del valor añadido de Macetech. Asimismo, al desacoplar el procesamiento de la ingesta de datos de las reglas de negocio, se posibilita la iteración continua en los modelos de decisión sin afectar los flujos de riego ni la analítica básica, favoreciendo la experimentación y el versionado de algoritmos. |
| Data Analytics   | Este módulo gestiona la ingesta, normalización y almacenamiento de los registros de sensores (SensorRecord), soporta tanto el procesamiento por lotes (batch) como en tiempo real (streaming) y provee dashboards analíticos para la visualización de métricas y tendencias relevantes.| **Consolidado:** Este módulo ofrece una visibilidad completa de las operaciones y sus resultados. Al aislarlo de la capa de control, se posibilita la escalabilidad de los pipelines de datos y la configuración de políticas de retención sin afectar los servicios transaccionales, lo que facilita la incorporación de nuevas herramientas de análisis.  |
| Caring Intelligence         | Este módulo integra un motor de recomendaciones que crea entidades Recommendation, soporta la generación de informes personalizados mediante plantillas (ReportTemplate) y emplea aprendizaje continuo para mejorar sus sugerencias de forma progresiva. | **Excluido:** En lugar de contar con un bounded context independiente para el motor de recomendaciones, se ha integrado completamente dentro del contexto de Service Operation and Monitoring. De este modo, las funciones de recomendación comparten la misma canalización de datos en tiempo real y los mecanismos de supervisión de dispositivos edge y embedded. Esta unificación reduce la latencia de la información y garantiza una única fuente para todas las reglas de negocio, facilitando al mismo tiempo el despliegue, la monitorización de desempeño y la iteración ágil de algoritmos sin impactar los flujos de riego ni los servicios de control. |
| Watering Management         | El motor de decisión de riego integra el análisis de los datos de los sensores (SensorData) y la configuración de la maceta (PotConfiguration) para generar automáticamente los trabajos de riego (IrrigationJob), gestionar posibles excepciones y coordinar su ejecución con la capa IoT. | **Excluido:** En lugar de mantener un bounded context independiente para el riego, esta responsabilidad se ha trasladado al nuevo contexto Service Operation and Monitoring. De este modo, las funciones de control físico, supervisión y excepción se agrupan junto con el resto de operaciones IoT, mejorando la cohesión y la claridad de la arquitectura. Asimismo, se ha prescindido de la planificación de riego tradicional, dado que el sistema opera exclusivamente en función de lecturas en tiempo real de los sensores, lo que simplifica el flujo de datos y evita duplicidades en la lógica de control. |
| Notifying System            | Este módulo se encarga del envío y la gestión de notificaciones genéricas, sin incluir información adicional ni vinculación con recomendaciones o alertas específicas. | **Excluido:** Su ámbito limitado, centrado exclusivamente en el envío de notificaciones genéricas, carecía de un modelo de datos sólido y presentaba solapamientos con las alertas críticas. Por ello, se ha integrado dentro del contexto de Service Operation and Monitoring, centralizando la supervisión y los canales de comunicación para eliminar la duplicación de lógica y reforzar la consistencia operativa. |
| Critical Alert System       | Se encarga de detectar y disparar alertas críticas basadas en umbrales específicos para las métricas de las plantas, garantizando una respuesta inmediata ante cualquier desviación que pueda comprometer su salud. | **Excluido:** Este componente duplicaba responsabilidades con el contexto de supervisión general y carecía de un modelo de datos y reglas propio. Por ello, su lógica se consolidó en «Service Operation and Monitoring», que centraliza y armoniza todas las alertas, eliminando redundancias y asegurando una única fuente de verdad. |
| AI Service | Servicio de inteligencia artificial orientado al procesamiento de datos, pero sin un enfoque claro en generar recomendaciones personalizadas para cada planta ni en la definición precisa de alertas, lo que limitaba su aplicabilidad directa dentro del flujo operativo. | **Excluido:** Este módulo resultaba excesivamente genérico y desalineado tanto de los casos de uso concretos como de los objetivos del proyecto. Se reemplazó por integraciones más focalizadas: la gestión de plantas recae ahora sobre la Plant API dentro del contexto de Service Design and Planning, mientras que la lógica de recomendaciones y el aprendizaje automático se integra por completo en Service Operation and Monitoring, asegurando un procesamiento de datos contextualizado, coherente y alineado con las necesidades operativas. |
| SensorState | Se encarga de la gestión remota del ciclo de vida y estado físico de los sensores, incluyendo calibración, detección de fallos y mantenimiento preventivo, para garantizar su operatividad continua y fiabilidad. | **Excluido:** La gestión remota de calibraciones, fallos y ciclos de vida de los sensores implicaba un dominio especializado en ingeniería de hardware que excedía el alcance principal del proyecto. Por ello, se optó por excluir este bounded context y conservar el foco en el desarrollo del software y la operatividad del sistema IoT. |

**7. Bounded Contexts finales**

Como resultado de la sesión de Candidate Context Discovery y tras identificar los eventos cruciales (pivotal events), se definieron y refinaron siete Bounded Contexts a partir de los candidatos iniciales. Para cada uno se establecieron sus responsabilidades principales, su lenguaje ubicuo y los contratos de integración, garantizando así una delimitación clara y coherente entre dominios.

###### Tabla 16

_Lista de Bounded Context finales identificados en el proceso de EventStorming de Macetech_

| Contexto | Responsabilidades clave | Ubiquitous Language  |
| ---------| ------------| -------- |
| **1. IAM**                         | **- Autenticación de usuarios:** gestión de inicio y cierre de sesión, con control seguro de las credenciales. <br>**- Emisión y validación de tokens:** generación de JSON Web Tokens (JWT) y tokens de refresco para mantener sesiones seguras y persistentes. <br> **- Autenticación de dos factores (2FA):** envío y verificación de códigos para reforzar la seguridad de acceso. <br> **- Gestión de permisos y roles:** definición, asignación y verificación de privilegios de usuario según políticas establecidas. <br> **- Registro y administración de cuentas:** creación de usuarios, recuperación de contraseñas y mantenimiento de perfiles. | **- User:** Representa a la persona real o entidad que interactúa con el sistema, identificada de forma única por un conjunto de atributos. <br> **- Credentials** Conjunto de datos secretos que el usuario emplea para demostrar su identidad.<br> **- Session:** Período de interacción autorizado entre un usuario y el sistema, iniciado tras la autenticación y mantenido mediante un token válido hasta que el usuario cierre sesión o expire. <br> **- Access Token:** Token de corta duración que certifica las credenciales del usuario y autoriza el acceso a recursos protegidos durante la sesión activa. <br> **- Refresh Token:** Token de mayor duración que permite obtener nuevos Access Tokens sin necesidad de que el usuario vuelva a autenticarse con sus credenciales. <br> **-Two‑Factor Authentication (2FA):** Mecanismo de seguridad adicional que exige un segundo factor de verificación (p. ej., código enviado por SMS o app de autenticación) tras la introducción de las credenciales. |
| **2. Profile & Personal Data**     | - **Gestión de perfil de usuario:** almacenamiento y actualización de datos personales (nombre, teléfono, dirección) con controles de integridad. <br> - **Configuración de preferencias:** personalización de idioma y modelo de notificaciones a recibir. <br> **- Integración con Geo API:** acceso a catálogos de países y ciudades para facilitar la selección y estandarización de ubicaciones. <br> - **Normalización y validación de direcciones:** aplicación de reglas y formatos estándar para asegurar la consistencia de los datos de ubicación. | - **User:** Representa al individuo registrado en el sistema, con una identidad única vinculada a su perfil y credenciales de acceso. <br> - **Profile:** Conjunto de datos personales y configuraciones asociadas a un usuario, incluyendo nombre, dirección, número de teléfono y preferencias. <br> - **Address:** Información estructurada sobre la ubicación física del usuario (país, ciudad, calle, código postal), sujeta a validación y normalización. <br> - **PhoneNumber:** Número de contacto del usuario, almacenado en formato internacional estandarizado y utilizado para verificación o notificaciones. <br> - **Preference:** Opciones personalizables elegidas por el usuario, como idioma, configuración de notificaciones, y tema de interfaz (modo claro/oscuro). <br> -**PasswordRecoveryToken:** Token temporal generado para permitir la recuperación segura de una cuenta en caso de pérdida de contraseña. - **GeoAPI:** Servicio externo que proporciona catálogos actualizados de países y ciudades para facilitar la selección geográfica y la validación de direcciones.      |
| **3. Asset & Resource Management**              | - **Gestión de macetas (Pot):** operaciones de creación, lectura, actualización y eliminación de instancias de Pot, garantizando la integridad y consistencia de los datos. <br> - **Configuración de riego:** definición de parámetros clave, como frecuencia, volumen y umbrales de activación, para adaptar el riego a las necesidades de cada planta. <br>- **Administración de metadatos:** asignación de atributos descriptivos (nombre, identificador único y etiquetas) que facilitan la organización, búsqueda y categorización de las macetas. <br> -**Registro histórico de configuraciones:** persistencia de todos los ajustes realizados en cada maceta, permitiendo auditorías y análisis de evolución a lo largo del tiempo. | - **Pot:** Representa la maceta física asociada a una planta, identificada por un ID único y un conjunto de atributos básicos.<br> -**PotConfiguration:** Conjunto de parámetros de riego y operación asignados a una maceta determinada (frecuencia, volumen, umbrales), que define cómo debe actuarse sobre ella. <br> -**Threshold:** Valor límite que, al ser superado por una medida (humedad, temperatura, etc.), desencadena una acción automática de riego o alerta. <br> -**Metadata:** Atributos descriptivos de la maceta, como nombre, etiquetas, fecha de creación, destinados a facilitar la búsqueda y categorización. <br> - **HistoricalConfig:** Registro inmutable de las configuraciones previas de la maceta, utilizado para auditoría y análisis de evolución en el tiempo. <br> -**SensorBinding:** Asociación de la maceta con uno o varios sensores específicos, que permite la ingestión de datos ambientales para toma de decisiones. <br> -**IrrigationJob:** Tarea disparada en tiempo real que ejecuta el acto de riego sobre la maceta, según su PotConfiguration y Thresholds.                   |
| **4. Service Design and Planning**  | -**Catálogo de especies vegetales (PlantSpecies):** Incluye los atributos técnicos de cada planta y sus rangos óptimos de pH, luminosidad, humedad, temperatura y salinidad, garantizando una base de datos exhaustiva para el cuidado botánico. <br> -**Validación de compatibilidad planta–maceta:** Comprueba que las características de la planta seleccionada se ajusten a las dimensiones y capacidades de la maceta, evitando errores de configuración y optimizando el desarrollo vegetal. <br> -**Sincronización con APIs externas:** Ejecuta actualizaciones periódicas para incorporar nuevas especies y refrescar parámetros existentes, asegurando que el catálogo se mantenga alineado con la información más reciente del sector. <br> -**Diseño y planificación del servicio:** Abarca desde la selección de la especie hasta la definición de sus parámetros personalizados,  incluyendo frecuencia y volumen de riego, y la programación de los horarios de riego, proporcionando un flujo de trabajo completo y coherente para la gestión automatizada de cada planta. | - **PlantSpecies:** Entidad que representa una especie vegetal, con atributos como nombre científico, nombre común y clasificación botánica. <br> - **OptimalRange:** Conjunto de valores óptimos para indicadores clave (pH, luminosidad, temperatura, salinidad, humedad) que definen el entorno ideal de crecimiento de una especie. <br> - **Compatibility:** Relación que valida la adecuación entre una especie y una maceta o ambiente determinado, asegurando que las condiciones físicas y de espacio sean apropiadas. <br> - **PlantAPI:** Servicio interno responsable de proporcionar catálogos de especies y actualizar parámetros botánicos de forma periódica. <br> - **PlantParameter:** Conjunto de parámetros personalizados vinculados a una instancia de PlantSpecies (por ejemplo, ajustes finos de frecuencia y volumen de riego). |
| **5. Service Operation and Monitoring** | -**Motor de decisión de riego:** analiza en tiempo real los datos de los sensores (SensorData) junto con la configuración de la maceta (PotConfiguration), generando automáticamente los trabajos de riego (IrrigationJob) y disparando las válvulas correspondientes. <br> - **Supervisión continua:** a través de health checks, registro y almacenamiento de logs críticos, envía datos de métricas de disponibilidad y rendimiento. <br> -**Sistema de alertas:** envía notificaciones (push, correo electrónico) ante umbrales o errores, garantizando respuestas inmediatas a incidentes. <br> -**Monitoreo de dispositivo embebido y edge:** integra la aplicación embebida y edge para garantizar la trazabilidad de cada componente y operación de la maceta (riego, alertas, recomendaciones). <br> -**Motor de recomendaciones:** sistema basado en reglas sobre los sensores de Pot y los datos obtenidos con PlantAPI, que crea entidades Recommendation mapeadas a patrones de uso y genera reportes personalizados (ReportTemplate). | - **IrrigationJob:** Tarea disparada en tiempo real que ejecuta el riego de una maceta, a partir de la configuración y los datos sensoriales. <br> - **ValveCommand:** Instrucción enviada al actuador de riego (válvula) para abrir o cerrar el flujo de agua según el plan de riego. <br> -**SensorData:** Lectura cruda proveniente de los sensores (humedad, temperatura, luminosidad, pH, etc.) asociada a una maceta en un instante de tiempo. <br> -**Alert:** Evento generado cuando una métrica o condición supera un umbral crítico, disparando un flujo de notificación y posibles acciones de mitigación. <br> -**NotificationChannel:** Medio utilizado para enviar alertas o avisos al usuario o al equipo de operaciones (push, correo electrónico). <br> -**Recommendation:** Sugerencia generada por el sistema de recomendaciones que propone acciones de cuidado o ajustes personalizados para la planta. <br> -**ReportTemplate:** Estructura predefinida que define el formato y contenido de los informes personalizados que se entregan al usuario. |
| **6. Subscriptions & Payments**    | **-Definición y gestión de planes de suscripción (SubscriptionPlan):** creación y parametrización de modalidades (freemium, premium mensual o anual), con reglas de acceso y beneficios asociados. <br> - **Procesamiento de pagos:** manejo de transacciones periódicas y cargos únicos, garantizando la fiabilidad y la seguridad en cada operación. <br> - **Administración de facturación (Invoice):** generación automática de facturas, seguimiento de su estado (pendiente, pagada, vencida) y emisión de recordatorios ante impagos. <br> -**Integración con pasarelas de pago y webhooks:** conexión con el proveedor externo de Stripe para la ejecución de pagos y recepción de notificaciones en tiempo real sobre eventos de cobro. | -**SubscriptionPlan:** Modelo que describe las modalidades de suscripción (freemium, premium mensual o anual), con sus características, precios y reglas de renovación. <br> -**Invoice:** Documento que detalla los cargos generados para un usuario, incluyendo desgloses de precio y fechas de vencimiento, así como su estado de pago. <br> -**PaymentTransaction:** Registro de cada intento de cobro o pago (recurrente o único), con información sobre el resultado y cualquier código de error. <br> -**Stripe API (PaymentGateway):** Servicio externo encargado de procesar los pagos, al que se envían las transacciones para su autorización y liquidación. <br> -**WebhookEvent:** Mensaje entrante desde la pasarela de pago que notifica al sistema sobre cambios en el estado de una transacción (aprobada, rechazada, reembolsada). <br> -**BillingCycle:** Periodo de facturación asociado a un SubscriptionPlan, que determina la cadencia de generación de Invoice y la programación de PaymentTransaction. |
| **7. Data Analytics**   | -**Ingesta, normalización y almacenamiento de registros de sensores (SensorRecord):** captura masiva de datos crudos, aplicación de procesos de limpieza y estructuración, y persistencia segura en el repositorio de datos. <br> -**Procesamiento batch y en streaming:** cálculo de métricas agregadas en lotes programados y en tiempo real, garantizando la disponibilidad continua de indicadores. <br> -**Exposición de dashboards y endpoints de consulta:** provisión de interfaces gráficas y APIs REST para la visualización interactiva de tendencias y la obtención directa de datos. - **Interpretación de KPIs:** elaboración de indicadores clave de rendimiento derivados de los datos sensoriales, facilitando la toma de decisiones operativas y estratégicas.                                        | -**SensorRecord:** Registro individual de datos capturados por un sensor (humedad, temperatura, luminosidad, pH, etc.), almacenado con su marca de tiempo y metadatos de origen. <br> -**InsightReport:** Documento generado a partir del análisis de los datos sensoriales y KPIs, que presenta conclusiones, tendencias y recomendaciones operativas o estratégicas. <br> -**Dashboard:** Interfaz gráfica interactiva que muestra visualizaciones en tiempo real o históricas de métricas clave, permitiendo filtrar y profundizar en la información. <br> -**BatchProcess:** Flujo de trabajo periódico que procesa grandes volúmenes de SensorRecord para calcular métricas agregadas y generar nuevos InsightReport. <br> -**KPI (Key Performance Indicator):** Métrica derivada de los datos sensoriales que cuantifica el rendimiento o estado de las macetas y plantas, usada para la toma de decisiones.
  |

#### 4.1.1.2 Domain Message Flows Modeling

En esta sección, el equipo presenta y documenta de forma detallada el proceso seguido para ilustrar la colaboración entre los distintos bounded contexts al abordar los casos de uso planteados por los usuarios del sistema. A través de la aplicación de la técnica de visualización Domain Storytelling, se evidenciará cada interacción y flujo de información entre los contextos, apoyándose en capturas de pantalla que muestran los diagramas elaborados durante el ejercicio. Este enfoque colaborativo permite validar y ajustar las fronteras de los dominios, garantizando que el diseño del software refleje fielmente las necesidades del negocio y del usuario.

Domain Storytelling es una técnica visual y ágil que utiliza historias narradas y representadas gráficamente para describir cómo los distintos actores y componentes del sistema interactúan en situaciones reales. Cada flujo se descompone en pasos secuenciales que combinan narración textual y símbolos estandarizados (actores, mensajes y artefactos), facilitando la comprensión colectiva y la detección temprana de inconsistencias o vacíos en el modelo de dominio (Hofer & Schwentner, 2021).

###### Figura 50

_Domain Storytelling del bounded context de Subscriptions and Payments_

<img src="/assets/img/capitulo-4/message-flows/message-flow-1.jpg" alt="MockUp" width="1000" height="500">

###### Figura 51

*Domain Storytelling de ...*

<img src="/assets/img/capitulo-4/message-flows/message-flow-2.jpg" alt="MockUp" width="1000" height="500"> 

###### Figura 52

_Domain Storytelling de ..._

<img src="/assets/img/capitulo-4/message-flows/message-flow-3.jpg" alt="MockUp" width="1000" height="500"> <

#### 4.1.1.3 Bounded Context Canvases

**IDENTITY AND ACCES MANAGEMENT**
<img src="/assets/img/capitulo-4/bounded-context-iam/Canvas.jpg" alt="MockUp" width="1000" height="500"> <br>

**Profile and personal data**
<img src="/assets/img/capitulo-4/bounded-context-profile-and-personal-data/Canvas2.jpg" alt="MockUp" width="1000" height="500"> <br>

### 4.1.2. Context Mapping

### 4.1.3. Software Architecture

La visión general de la arquitectura describe la estructura fundamental de un sistema, abarcando sus componentes principales y la interacción entre ellos. En el contexto de desarrollo de aplicaciones móviles, una arquitectura sólida es esencial para garantizar que la aplicación sea escalable, segura y eficiente. Este enfoque permite una implementación ordenada, donde cada parte del sistema tiene una responsabilidad clara, y facilita la integración de nuevas funcionalidades o la modificación de las existentes sin afectar la estabilidad general de la plataforma (Richards & Ford, 2021).

El diseño arquitectónico de la aplicación móvil Roademics se basa en una arquitectura modular, donde cada componente del sistema está desacoplado, permitiendo un desarrollo y mantenimiento más flexible. Este enfoque se apoya en patrones de diseño como el Modelo-Vista-Controlador (MVC) y el Modelo-Vista-ViewModel (MVVM), que promueven una clara separación de preocupaciones y mejoran la mantenibilidad del código. Además, se integra con servicios externos de autenticación, bases de datos en la nube, y plataformas de análisis, asegurando que la aplicación pueda manejar grandes volúmenes de datos de manera eficiente y con una alta disponibilidad.

La arquitectura también contempla la seguridad como un aspecto central, con la implementación de técnicas de cifrado para proteger los datos sensibles del usuario y garantizar que las comunicaciones dentro de la aplicación sean seguras. Además, se diseña para ser compatible con diversas plataformas móviles, adaptándose a las especificaciones de iOS y Android, lo que facilita una experiencia de usuario consistente y de alta calidad en ambos entornos.

De acuerdo con Brown (2023), el modelo C4 para la diagramación y esquematización de la arquitectura de software ofrece un enfoque estructurado y escalable que facilita la descripción clara de sus secciones y componentes. Al dividir la arquitectura en cuatro niveles —Contexto, Contenedores, Componentes y Código—, permite una comprensión más accesible tanto para técnicos como para partes interesadas sin experiencia técnica. Esta estructura promueve una comunicación más fluida y efectiva entre los equipos de desarrollo y las partes involucradas, optimizando el proceso colaborativo y resultando en un desarrollo más eficiente y en una arquitectura de software más robusta y mantenible.

<image src="../assets/img/capitulo-4/c4-model/structurizr-101667-container-view-key.png"></image>

#### 4.1.3.1. Software Architecture System Landscape Diagram.

El diagrama de landscape (o paisaje del sistema) representa un nivel organizacional dentro del modelo C4, proporcionando una visión holística de todos los sistemas de software relevantes y cómo se relacionan entre sí dentro de un entorno empresarial o tecnológico más amplio. Este diagrama ayuda a comprender la arquitectura distribuida de múltiples sistemas, ya sean internos o externos, y las interacciones clave que sostienen los flujos de información entre ellos.

En el contexto de una plataforma de jardinería inteligente como Macetech, el diagrama de landscape muestra cómo conviven e interactúan los distintos sistemas que conforman el ecosistema completo: desde las aplicaciones cliente (web, móvil), el backend monolítico, y los servicios embebidos en dispositivos IoT, hasta los sistemas externos como APIs de inteligencia artificial. Esta representación permite identificar relaciones críticas entre componentes distribuidos, dependencias tecnológicas y oportunidades de desacoplamiento, facilitando tanto la toma de decisiones arquitectónicas como la evolución escalable del sistema.

<image src="../assets/img/capitulo-4/c4-model/structurizr-101667-landing-page-components-diagram.png"></image>

#### 4.1.3.2. Software Architecture Context Level Diagrams.

El diagrama de contexto, el nivel más alto de abstracción en el modelo C4, proporciona una vista general del sistema y su entorno externo, ilustrando las interacciones de alto nivel entre el sistema y los actores externos. Este diagrama ofrece una representación clara de cómo el sistema se relaciona con sus usuarios, agentes externos y otros componentes ajenos al sistema.

En el caso de una aplicación web inmobiliaria, el diagrama de contexto muestra de manera detallada las interacciones entre los usuarios finales, los agentes inmobiliarios y la plataforma. Además, destaca las conexiones críticas entre la aplicación y diversas API y servicios externos, esenciales para habilitar las funcionalidades clave que la plataforma debe ofrecer a los usuarios. Estas integraciones son fundamentales para garantizar una experiencia fluida y robusta, respondiendo a las necesidades dinámicas del mercado inmobiliario.

<image src="../assets/img/capitulo-4/c4-model/structurizr-101667-system-context.png"></image>

#### 4.1.3.2. Software Architecture Container Level Diagrams.

El diagrama de contenedores ofrece una representación visual detallada de la arquitectura interna de un sistema de software, mostrando los principales contenedores (como aplicaciones, bases de datos o servicios) y cómo estos se comunican para cumplir con los objetivos del sistema. Es una herramienta esencial para facilitar la comprensión de la estructura y las interacciones internas, permitiendo a los miembros del equipo técnico y otras partes interesadas colaborar de manera más eficiente.

En el caso del sistema integrado de Roademics, este diagrama desglosa la arquitectura, revelando las conexiones entre los distintos puntos de desarrollo, así como las interacciones con sistemas externos adyacentes. A través del BackEnd, se establecen conexiones directas con la base de datos, la cual gestiona y almacena la información crítica para el funcionamiento eficiente del sistema. Este enfoque detallado permite una visión clara de cómo cada componente colabora para brindar una experiencia fluida y coherente, asegurando que todas las partes del sistema trabajen en conjunto de manera efectiva.

<image src="../assets/img/capitulo-4/c4-model/structurizr-101667-container-view.png"></image>

#### 4.1.3.3. Software Architecture Deployment Diagrams.

## 4.2. Tactical-Level Domain-Driven Design

### 4.2.1. Bounded Context: IAM (Identity and Access Management)

#### 4.2.1.1. Domain Layer.

## User

| Propiedad     | Valor                       |
| ------------- | --------------------------- |
| **Nombre**    | User                        |
| **Categoría** | Aggregate Root              |
| **Propósito** | Almacenar datos del usuario |

---

### Atributos

| Nombre      | Tipo de dato    | Visibilidad | Descripción                                  |
| ----------- | --------------- | ----------- | -------------------------------------------- |
| Id          | `unsigned long` | private     | Identificador irrepetible del usuario        |
| FullName    | `FullName`      | private     | Nombres del usuario                          |
| Email       | `Email`         | private     | Correo electrónico del usuario               |
| Password    | `PasswordHash`  | private     | Lógica de hashing/verificación de contraseña |
| Role        | `List<Role>`    | private     | Rol del usuario                              |
| CreatedDate | `DateTime`      | private     | Fecha de creación del usuario                |
| Status      | `Status` (enum) | private     | Estado del usuario                           |

---

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                            |
| -------------- | --------------- | ----------- | -------------------------------------- |
| ChangeName     | `void`          | public      | Cambiar nombre del usuario             |
| ChangeEmail    | `void`          | public      | Cambiar correo electrónico del usuario |
| ChangePassword | `void`          | public      | Cambiar contraseña del usuario         |
| ChangeRole     | `void`          | public      | Cambiar el rol del usuario             |
| Suspend        | `void`          | public      | Suspender al usuario                   |
| Activate       | `void`          | public      | Reactiva al usuario                    |
| Delete         | `void`          | public      | Marcar al usuario como eliminado       |

## UserId

| Propiedad     | Valor                                        |
| ------------- | -------------------------------------------- |
| **Nombre**    | UserId                                       |
| **Categoría** | Value Object                                 |
| **Propósito** | Encapsular el identificador único de usuario |

### Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción                    |
| ------ | ------------ | ----------- | ------------------------------ |
| Value  | `Long`       | private     | Identificador único de usuario |

---

## FullName

| Propiedad     | Valor                        |
| ------------- | ---------------------------- |
| **Nombre**    | FullName                     |
| **Categoría** | Value Object                 |
| **Propósito** | Almacenar nombres de usuario |

### Atributos

| Nombre    | Tipo de dato | Visibilidad | Descripción           |
| --------- | ------------ | ----------- | --------------------- |
| name      | `string`     | private     | Nombre del usuario    |
| LastNames | `string`     | private     | Apellidos del usuario |

---

## Email

| Propiedad     | Valor                                       |
| ------------- | ------------------------------------------- |
| **Nombre**    | Email                                       |
| **Categoría** | Value Object                                |
| **Propósito** | Almacenar el correo electrónico del usuario |

### Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción                    |
| ------ | ------------ | ----------- | ------------------------------ |
| Email  | `string`     | private     | Correo electrónico del usuario |

## PasswordHash

| Propiedad     | Valor                                       |
| ------------- | ------------------------------------------- |
| **Nombre**    | PasswordHash                                |
| **Categoría** | Value Object                                |
| **Propósito** | Almacenar el correo electrónico del usuario |

### Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción                    |
| ------ | ------------ | ----------- | ------------------------------ |
| email  | `string`     | private     | Correo electrónico del usuario |

### Métodos

| Nombre  | Tipo de retorno | Visibilidad | Descripción                                  |
| ------- | --------------- | ----------- | -------------------------------------------- |
| Matches | `bool`          | public      | Verificar si un texto coincide con este hash |

---

## UserFactory

| Propiedad     | Valor                             |
| ------------- | --------------------------------- |
| **Nombre**    | UserFactory                       |
| **Categoría** | Factory                           |
| **Propósito** | Crear nuevas instancias de `User` |

### Métodos

| Nombre | Tipo de retorno | Visibilidad | Descripción                   |
| ------ | --------------- | ----------- | ----------------------------- |
| Create | `User`          | public      | Crear una instancia de `User` |

## IUserRepository

| Propiedad     | Valor                                   |
| ------------- | --------------------------------------- |
| **Nombre**    | IUserRepository                         |
| **Categoría** | Repository                              |
| **Propósito** | Persistir y consultar entidades de User |

### Métodos

| Nombre               | Tipo de retorno | Visibilidad | Descripción                                                   |
| -------------------- | --------------- | ----------- | ------------------------------------------------------------- |
| GetByIdAsync         | `User?`         | public      | Obtener un usuario por identificador                          |
| FindByEmailAsync     | `User?`         | public      | Buscar un usuario por correo                                  |
| ExistsByEmailAsync   | `bool`          | public      | Verificar si hay un usuario con dicho email ya registrado     |
| FindAllAsync         | `List<User>`    | public      | Lista de usuarios (para casos de administración)              |
| SaveAsync            | `User`          | public      | Crear o actualizar un usuario; devuelve la entidad persistida |
| DeleteLogicallyAsync | `bool`          | public      | Elimina lógicamente un usuario                                |
| CountAsync           | `long`          | public      | Total de usuarios                                             |

---

## ISessionRepository

| Propiedad     | Valor                                   |
| ------------- | --------------------------------------- |
| **Nombre**    | ISessionRepository                      |
| **Categoría** | Repository                              |
| **Propósito** | Persistir y consultar entidades de User |

### Métodos

| Nombre                  | Tipo de retorno | Visibilidad | Descripción                                  |
| ----------------------- | --------------- | ----------- | -------------------------------------------- |
| FindByTokenId           | `SessionToken?` | public      | Obtener un SessionToken por identificador    |
| Store                   | `void`          | public      | Guardar un SessionToken activo               |
| Revoke                  | `void`          | public      | Revocar un token                             |
| RevokeAllSessionForUser | `void`          | public      | Revocar todas los SessionToken de un usuario |

## Authenticator

| Propiedad     | Valor                                    |
| ------------- | ---------------------------------------- |
| **Nombre**    | Authenticator                            |
| **Categoría** | Domain Service                           |
| **Propósito** | Verificar las credenciales de un usuario |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                                                         |
| ------------ | --------------- | ----------- | ------------------------------------------------------------------- |
| authenticate | `SessionToken`  | public      | Valida las credenciales de un usuario y devuelve un token de sesión |

---

## SessionToken

| Propiedad     | Valor                                       |
| ------------- | ------------------------------------------- |
| **Nombre**    | SessionToken                                |
| **Categoría** | Entity                                      |
| **Propósito** | Representar una sesión activa de un usuario |

### Atributos

| Nombre    | Tipo de dato | Visibilidad | Descripción                          |
| --------- | ------------ | ----------- | ------------------------------------ |
| TokenId   | `string`     | private     | Identificador único del token        |
| userId    | `UserId`     | private     | Identificador del usuario            |
| createdAt | `DateTime`   | private     | Fecha y hora de creación del token   |
| expiresAt | `DateTime`   | private     | Fecha y hora de expiración del token |
| revoked   | `bool`       | private     | Indica si el token ha sido revocado  |

#### 4.2.1.2. Interface Layer.

## UserController

| Propiedad     | Valor              |
| ------------- | ------------------ |
| **Nombre**    | UserController     |
| **Categoría** | Controller         |
| **Propósito** | Gestionar usuarios |
| **Ruta**      | `/api/users`       |

### Métodos

| Nombre         | Ruta                 | Acción                          | Handle                                                           |
| -------------- | -------------------- | ------------------------------- | ---------------------------------------------------------------- |
| GetById        | `/{userId}`          | Obtiene información del usuario | `GetUserByIdQuery`                                               |
| ChangeName     | `/{userId}/name`     | Cambia `FullName`               | `ChangeUserNameCommand`                                          |
| ChangeEmail    | `/{userId}/email`    | Cambia `Email`                  | `ChangeUserEmailCommand`                                         |
| ChangePassword | `/{userId}/password` | Cambia `PasswordHash`           | `ChangeUserPasswordCommand`                                      |
| ChangeStatus   | `/{userId}/status`   | Cambia `Status`                 | `ActivateUserCommand`, `SuspendUserCommand`, `DeleteUserCommand` |

---

## AuthController

| Propiedad     | Valor                                                         |
| ------------- | ------------------------------------------------------------- |
| **Nombre**    | AuthController                                                |
| **Categoría** | Controller                                                    |
| **Propósito** | Encargado de todo lo relacionado con registro y autenticación |
| **Ruta**      | `/api/auth`                                                   |

### Métodos

| Nombre   | Ruta        | Acción                               | Handle                 |
| -------- | ----------- | ------------------------------------ | ---------------------- |
| Register | `/register` | Crea un nuevo usuario                | `RegisterUserCommand`  |
| Login    | `/login`    | Valida credenciales y devuelve token | `LoginUserCommand`     |
| Refresh  | `/refresh`  | Renueva el acceso; nuevo token       | `~`                    |
| Logout   | `/logout`   | Revoca el token activo               | `RevokeSessionCommand` |

#### 4.2.1.3. Application Layer.

## UserRegisterCommandHandler

| Propiedad     | Valor                      |
| ------------- | -------------------------- |
| **Nombre**    | UserRegisterCommandHandler |
| **Categoría** | Command Handler            |
| **Propósito** | Registrar un usuario       |
| **Comando**   | RegisterUserCommand        |

---

## UserLoginCommandHandler

| Propiedad     | Valor                       |
| ------------- | --------------------------- |
| **Nombre**    | UserLoginCommandHandler     |
| **Categoría** | Command Handler             |
| **Propósito** | Iniciar sesión a un usuario |
| **Comando**   | LoginUserCommand            |

---

## UserLogoutCommandHandler

| Propiedad     | Valor                       |
| ------------- | --------------------------- |
| **Nombre**    | UserLogoutCommandHandler    |
| **Categoría** | Command Handler             |
| **Propósito** | Cerrar sesión de un usuario |
| **Comando**   | LogoutUserCommand           |

---

## RegisteredUserEventHandler

| Propiedad     | Valor                               |
| ------------- | ----------------------------------- |
| **Nombre**    | RegisteredUserEventHandler          |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserRegisteredEvent                 |

---

## UserLoggedInEventHandler

| Propiedad     | Valor                               |
| ------------- | ----------------------------------- |
| **Nombre**    | UserLoggedInEventHandler            |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserLoggedInEvent                   |

---

## UserLoggedOutEventHandler

| Propiedad     | Valor                               |
| ------------- | ----------------------------------- |
| **Nombre**    | UserLoggedOutEventHandler           |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserLoggedOutEvent                  |

#### 4.2.1.4. Infrastructure Layer.

## UserRepository

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | UserRepository                            |
| **Categoría** | Repositorio                               |
| **Propósito** | Persistir y consultar entidades de `User` |
| **Interfaz**  | `IUserRepository`                         |

---

## SessionRepository

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | SessionRepository                         |
| **Categoría** | Repositorio                               |
| **Propósito** | Persistir y consultar entidades de `User` |
| **Interfaz**  | `ISessionRepository`                      |

---

## AppDbContext

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | AppDbContext                               |
| **Categoría** | ORM Context                                |
| **Propósito** | Punto central de acceso a la base de datos |

#### 4.2.1.5. Bounded Context Software Architecture Component Level Diagrams.

El diagrama de componentes profundiza aún más en la arquitectura de un sistema, desglosando cada contenedor en sus componentes individuales. Este nivel de análisis permite una representación clara y detallada de la organización interna, así como de la comunicación entre estos componentes dentro de cada contenedor, facilitando una comprensión precisa de cómo interactúan y se interrelacionan para cumplir las funciones del sistema.

En el contexto de Roademics, el diagrama de componentes destaca los elementos clave del backend, con especial énfasis en el controlador principal, que actúa como el núcleo organizador. Este controlador es responsable de coordinar y orquestar las operaciones internas, gestionando los flujos de datos y asegurando la interacción eficiente con componentes especializados, tales como aquellos que manejan la interacción con APIs externas y las conexiones a la base de datos. Al ilustrar estas interacciones, se obtiene una visión detallada de cómo los diferentes componentes colaboran para mantener la integridad y funcionalidad del sistema.

La utilidad del diagrama de componentes se extiende más allá del simple entendimiento de la arquitectura. Al proporcionar una visualización clara de cómo se gestionan los datos dentro de la aplicación móvil, este diagrama resulta invaluable no solo para los desarrolladores, sino también para los equipos de mantenimiento y actualización del sistema. Al descomponer cada elemento en sus componentes individuales y mapear sus interacciones, el diagrama optimiza el proceso de diseño y desarrollo, facilitando un mantenimiento efectivo y minimizando la complejidad durante el ciclo de vida del software.

<image src="../assets/img/capitulo-4/c4-model/structurizr-101667-monolith-components-diagram.png"></image>

<image src="../assets/img/capitulo-4/c4-model/structurizr-101667-wca-components-diagram.png"></image>

<image src="../assets/img/capitulo-4/c4-model/structurizr-101667-mobile-app-components-diagram.png"></image>

<image src="../assets/img/capitulo-4/c4-model/structurizr-101667-edge-application-diagram.png"></image>

<image src="../assets/img/capitulo-4/c4-model/structurizr-101667-embedded-application-diagram.png"></image>

#### 4.2.1.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.1.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-iam/class-diagram.png"></image>

##### 4.2.1.6.2. Bounded Context Database Design Diagram.

<image src="../assets/img/capitulo-4/bounded-context-iam/database-diagram.png"></image>

### 4.2.2. Bounded Context: Profile and Personal Data

#### 4.2.2.1. Domain Layer.

## Profile

| Propiedad     | Valor                                                              |
| ------------- | ------------------------------------------------------------------ |
| **Nombre**    | Profile                                                            |
| **Categoría** | Aggregate Root                                                     |
| **Propósito** | Agrupar y gestionar los datos de perfil y personales de un usuario |

### Atributos

| Nombre           | Tipo de dato    | Visibilidad | Descripción                                         |
| ---------------- | --------------- | ----------- | --------------------------------------------------- |
| userUid          | `String`        | private     | Identificador único del usuario                     |
| name             | `FullName`      | private     | Nombre completo del usuario                         |
| phoneNumber      | `PhoneNumber`   | private     | Número de teléfono del usuario                      |
| streetAddress    | `StreetAddress` | private     | Dirección física del usuario                        |
| profileRole      | `ProfileRole`   | private     | Rol asignado al perfil (Amateur o Gardener)         |
| imageUrl         | `String`        | private     | URL de la imagen de perfil                          |
| notifyUsingEmail | `Boolean`       | private     | Indica si el usuario desea notificaciones por email |
| createdAt        | `DateTime`      | private     | Fecha de creación del perfil                        |
| updatedAt        | `DateTime`      | private     | Fecha de la última actualización del perfil         |

### Métodos

| Nombre                  | Tipo de retorno | Visibilidad | Descripción                                             |
| ----------------------- | --------------- | ----------- | ------------------------------------------------------- |
| changeName              | `void`          | public      | Actualiza el `name` y marca `updatedAt`                 |
| changePhoneNumber       | `void`          | public      | Actualiza el `phoneNumber` y marca `updatedAt`          |
| changeStreetAddress     | `void`          | public      | Actualiza el `streetAddress` y marca `updatedAt`        |
| setProfileImage         | `void`          | public      | Actualiza el `imageUrl` y marca `updatedAt`             |
| toggleEmailNotification | `void`          | public      | Activa/desactiva `notifyUsingEmail` y marca `updatedAt` |
| markUpdated             | `void`          | private     | Actualiza internamente el campo `updatedAt`             |

## FullName

| Propiedad     | Valor                                    |
| ------------- | ---------------------------------------- |
| **Nombre**    | FullName                                 |
| **Categoría** | Value Object                             |
| **Propósito** | Encapsular nombre y apellido del usuario |

### Atributos

| Nombre   | Tipo de dato | Visibilidad | Descripción           |
| -------- | ------------ | ----------- | --------------------- |
| name     | `String`     | private     | Nombre propio         |
| lastName | `String`     | private     | Apellidos del usuario |

### Métodos

| Nombre   | Tipo de retorno | Visibilidad | Descripción                     |
| -------- | --------------- | ----------- | ------------------------------- |
| fullName | `String`        | public      | Retorna `name + " " + lastName` |

## PhoneNumber

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | PhoneNumber                               |
| **Categoría** | Value Object                              |
| **Propósito** | Validar y almacenar un número de teléfono |

### Atributos

| Nombre      | Tipo de dato | Visibilidad | Descripción                |
| ----------- | ------------ | ----------- | -------------------------- |
| countryCode | `String`     | private     | Código de país (ej. "+51") |
| number      | `String`     | private     | Número local del teléfono  |

### Métodos

| Nombre    | Tipo de retorno | Visibilidad | Descripción                     |
| --------- | --------------- | ----------- | ------------------------------- |
| formatted | `String`        | public      | Devuelve `countryCode + number` |

## StreetAddress

| Propiedad     | Valor                                  |
| ------------- | -------------------------------------- |
| **Nombre**    | StreetAddress                          |
| **Categoría** | Value Object                           |
| **Propósito** | Almacenar datos de la dirección física |

### Atributos

| Nombre       | Tipo de dato | Visibilidad | Descripción                        |
| ------------ | ------------ | ----------- | ---------------------------------- |
| street       | `String`     | private     | Nombre de la calle                 |
| streetNumber | `String`     | private     | Número o identificador de la calle |
| city         | `String`     | private     | Ciudad                             |
| postalCode   | `String`     | private     | Código postal                      |
| country      | `String`     | private     | País                               |

### Métodos

| Nombre      | Tipo de retorno | Visibilidad | Descripción                                               |
| ----------- | --------------- | ----------- | --------------------------------------------------------- |
| fullAddress | `String`        | public      | Retorna la concatenación de todos los campos de dirección |

## ProfileRole

| Propiedad     | Valor                                   |
| ------------- | --------------------------------------- |
| **Nombre**    | ProfileRole                             |
| **Categoría** | Enum                                    |
| **Propósito** | Definir los posibles roles de un perfil |

### Valores

| Valor    | Descripción                 |
| -------- | --------------------------- |
| Amateur  | Perfil de usuario amateur   |
| Gardener | Perfil de usuario jardinero |

## ProfileFactory

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | ProfileFactory                            |
| **Categoría** | Factory                                   |
| **Propósito** | Construir instancias válidas de `Profile` |

### Métodos

| Nombre | Tipo de retorno | Visibilidad | Descripción                                                                                       |
| ------ | --------------- | ----------- | ------------------------------------------------------------------------------------------------- |
| create | `Profile`       | public      | Crea un `Profile` a partir de datos primitivos, valida valores y asigna `createdAt` y `updatedAt` |

## IProfileRepository

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | IProfileRepository                        |
| **Categoría** | Repository                                |
| **Propósito** | Persistir y recuperar entidades `Profile` |

### Métodos

| Nombre        | Tipo de retorno | Visibilidad | Descripción                                       |
| ------------- | --------------- | ----------- | ------------------------------------------------- |
| findById      | `Profile?`      | public      | Recupera un perfil según su identificador interno |
| findByUserUid | `Profile?`      | public      | Recupera un perfil según `userUid`                |
| create        | `Unit`          | public      | Persiste un nuevo `Profile`                       |
| update        | `Unit`          | public      | Actualiza un `Profile` existente                  |
| delete        | `Unit`          | public      | Elimina lógicamente un `Profile`                  |

#### 4.2.2.2. Interface Layer.

## ProfileController

| Propiedad     | Valor                             |
| ------------- | --------------------------------- |
| **Nombre**    | ProfileController                 |
| **Categoría** | Controller                        |
| **Propósito** | Exponer servicios REST de Profile |
| **Ruta**      | `/api/profile/`                   |

### Métodos

| Nombre                   | Ruta                 | Acción                     | Handle                            |
| ------------------------ | -------------------- | -------------------------- | --------------------------------- |
| getProfile               | `/{uid}`             | Obtener perfil             | `GetProfileQuery`                 |
| updateProfile            | `/{uid}`             | Actualizar perfil completo | `UpdateProfileCommand`            |
| deleteProfile            | `/{uid}`             | Eliminar perfil            | `DeleteProfileCommand`            |
| createProfile            | `/create`            | Crear nuevo perfil         | `CreateProfileCommand`            |
| updateProfilePreferences | `/preferences/{uid}` | Actualizar preferencias    | `UpdateProfilePreferencesCommand` |

#### 4.2.2.3. Application Layer.

## GetProfileQueryHandler

| Propiedad     | Valor                                    |
| ------------- | ---------------------------------------- |
| **Nombre**    | GetProfileQueryHandler                   |
| **Categoría** | Query Handler                            |
| **Propósito** | Manejar la lógica para `GetProfileQuery` |

## CreateProfileCommandHandler

| Propiedad     | Valor                                                      |
| ------------- | ---------------------------------------------------------- |
| **Nombre**    | CreateProfileCommandHandler                                |
| **Categoría** | Command Handler                                            |
| **Propósito** | Ejecutar la creación de un perfil (`CreateProfileCommand`) |

## UpdateProfileCommandHandler

| Propiedad     | Valor                                                           |
| ------------- | --------------------------------------------------------------- |
| **Nombre**    | UpdateProfileCommandHandler                                     |
| **Categoría** | Command Handler                                                 |
| **Propósito** | Ejecutar la actualización de un perfil (`UpdateProfileCommand`) |

## DeleteProfileCommandHandler

| Propiedad     | Valor                                                         |
| ------------- | ------------------------------------------------------------- |
| **Nombre**    | DeleteProfileCommandHandler                                   |
| **Categoría** | Command Handler                                               |
| **Propósito** | Ejecutar la eliminación de un perfil (`DeleteProfileCommand`) |

## UpdateProfilePreferencesCommandHandler

| Propiedad     | Valor                                                                                   |
| ------------- | --------------------------------------------------------------------------------------- |
| **Nombre**    | UpdateProfilePreferencesCommandHandler                                                  |
| **Categoría** | Command Handler                                                                         |
| **Propósito** | Ejecutar la actualización de preferencias de perfil (`UpdateProfilePreferencesCommand`) |

## CreatedProfileEventHandler

| Propiedad     | Valor                                                   |
| ------------- | ------------------------------------------------------- |
| **Nombre**    | CreatedProfileEventHandler                              |
| **Categoría** | Event Handler                                           |
| **Propósito** | Procesar la lógica tras el evento `ProfileCreatedEvent` |

## UpdatedProfileEventHandler

| Propiedad     | Valor                                                   |
| ------------- | ------------------------------------------------------- |
| **Nombre**    | UpdatedProfileEventHandler                              |
| **Categoría** | Event Handler                                           |
| **Propósito** | Procesar la lógica tras el evento `ProfileUpdatedEvent` |

## DeletedProfileEventHandler

| Propiedad     | Valor                                                   |
| ------------- | ------------------------------------------------------- |
| **Nombre**    | DeletedProfileEventHandler                              |
| **Categoría** | Event Handler                                           |
| **Propósito** | Procesar la lógica tras el evento `ProfileDeletedEvent` |

#### 4.2.2.4. Infrastructure Layer.

## ProfileRepository

| Propiedad     | Valor                                                  |
| ------------- | ------------------------------------------------------ |
| **Nombre**    | ProfileRepository                                      |
| **Categoría** | Repository Implementation                              |
| **Propósito** | Implementar `IProfileRepository` usando ORM relacional |
| **Interfaz**  | `IProfileRepository`                                   |

#### 4.2.2.5. Bounded Context Software Architecture Component Level Diagrams.

[missing-res]

#### 4.2.2.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.2.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-profile-and-personal-data/class-diagram-profile-and-personal-data.png"></image>

##### 4.2.2.6.2. Bounded Context Database Design Diagram.

<image src="../assets/img/capitulo-4/bounded-context-profile-and-personal-data/database-diagram-profile-and-personal-data.png"></image>

## 4.2.3. Bounded Context: Asset and Resource Management

---

### 4.2.3.1. Domain Layer

#### SmartPot

| Propiedad     | Valor                                         |
| ------------- | --------------------------------------------- |
| **Nombre**    | SmartPot                                      |
| **Categoría** | Aggregate Root                                |
| **Propósito** | Representa una maceta inteligente del usuario |

##### Atributos

| Nombre                 | Tipo de dato              | Visibilidad | Descripción                              |
| ---------------------- | ------------------------- | ----------- | ---------------------------------------- |
| Id                     | `Guid`                    | private     | Identificador único de la maceta         |
| Nombre                 | `string`                  | private     | Nombre asignado por el usuario           |
| Tipo                   | `string`                  | private     | Tipo de planta (ej. suculenta, tropical) |
| Ubicacion              | `string`                  | private     | Ubicación física                         |
| Estado                 | `EstadoMaceta`            | private     | Enum: Saludable, Atencion, Critica       |
| FechaRegistro          | `DateTime`                | private     | Fecha de alta                            |
| DispositivoBluetoothId | `string?`                 | private     | ID de dispositivo BLE (si aplica)        |
| UuidFabricacion        | `string`                  | private     | Código de fabricación                    |
| UsuarioId              | `Guid`                    | private     | Identificador de usuario propietario     |
| ConfiguracionRiego     | `ConfiguracionRiego`      | private     | Configuración de riego de la maceta      |
| HistorialRiego         | `List<HistorialRiego>`    | private     | Registros de riegos                      |
| Telemetrias            | `List<LecturaTelemetria>` | private     | Telemetrías asociadas                    |
| Alertas                | `List<Alerta>`            | private     | Alertas críticas o warnings              |

##### Métodos

| Nombre               | Tipo de retorno  | Descripción                                         |
| -------------------- | ---------------- | --------------------------------------------------- |
| Editar               | `void`           | Modifica nombre, tipo o ubicación                   |
| CambiarEstado        | `void`           | Actualiza el estado según las condiciones           |
| AsignarBluetoothId   | `void`           | Registra el ID BLE para vinculación                 |
| AsignarUUID          | `void`           | Asocia el UUID de fabricación                       |
| Eliminar             | `void`           | Marca la maceta como inactiva                       |
| RegistrarRiegoManual | `HistorialRiego` | Agrega un evento de riego manual                    |
| PuedeAgregarRiego    | `bool`           | Verifica si puede regarse (según reglas de negocio) |

---

#### ConfiguracionRiego

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | ConfiguracionRiego                        |
| **Categoría** | Entidad anidada                           |
| **Propósito** | Parámetros de riego asociados a la maceta |

##### Atributos

| Nombre         | Tipo de dato | Visibilidad | Descripción                      |
| -------------- | ------------ | ----------- | -------------------------------- |
| FrecuenciaDias | `int`        | private     | Días entre riegos                |
| CantidadML     | `float`      | private     | Cantidad de agua por sesión (ml) |
| HoraProgramada | `TimeSpan`   | private     | Hora del riego automático        |
| Modo           | `ModoRiego`  | private     | Enum: Automatico, Manual, Mixto  |

---

#### Usuario

| Propiedad     | Valor                              |
| ------------- | ---------------------------------- |
| **Nombre**    | Usuario                            |
| **Categoría** | Referencia externa                 |
| **Propósito** | Representa al dueño de las macetas |

---

#### HistorialRiego

| Propiedad        | Tipo de dato | Visibilidad | Descripción                    |
| ---------------- | ------------ | ----------- | ------------------------------ |
| Id               | `Guid`       | private     | Identificador único            |
| SmartPotId       | `Guid`       | private     | FK hacia SmartPot              |
| Fecha            | `DateTime`   | private     | Fecha y hora del riego         |
| DuracionSegundos | `int`        | private     | Duración del riego             |
| VolumenAguaML    | `int`        | private     | Volumen de agua usado (ml)     |
| HumedadInicial   | `int`        | private     | Humedad antes del riego        |
| HumedadFinal     | `int`        | private     | Humedad después del riego      |
| Resultado        | `string`     | private     | Resultado (éxito, error, etc.) |

---

#### LecturaTelemetria

| Propiedad       | Tipo de dato | Visibilidad | Descripción               |
| --------------- | ------------ | ----------- | ------------------------- |
| Id              | `Guid`       | private     | Identificador único       |
| SmartPotId      | `Guid`       | private     | FK hacia SmartPot         |
| Timestamp       | `DateTime`   | private     | Fecha de la medición      |
| Humedad         | `float`      | private     | Porcentaje de humedad     |
| Ph              | `float`      | private     | Nivel de acidez           |
| Salinidad       | `float`      | private     | Salinidad del sustrato    |
| Temperatura     | `float`      | private     | Temperatura               |
| ExposicionSolar | `bool?`      | private     | Exposición anómala        |
| HorasExposicion | `int?`       | private     | Horas de exposición solar |

---

#### Alerta

| Propiedad      | Tipo de dato | Visibilidad | Descripción                     |
| -------------- | ------------ | ----------- | ------------------------------- |
| Id             | `Guid`       | private     | Identificador único             |
| SmartPotId     | `Guid`       | private     | FK hacia SmartPot               |
| Tipo           | `string`     | private     | Tipo de alerta                  |
| ValorDetectado | `float`      | private     | Valor que generó la alerta      |
| Urgencia       | `string`     | private     | Nivel de urgencia               |
| Recomendacion  | `string`     | private     | Sugerencia o acción recomendada |
| GuiaUrl        | `string`     | private     | Enlace a guía externa           |

---

### 4.2.3.2. Interface Layer

#### DTOs y Requests/Responses

| DTO/Record             | Campos principales                                                                   | Propósito          |
| ---------------------- | ------------------------------------------------------------------------------------ | ------------------ |
| `SmartPotSummaryDto`   | Id, Nombre, Tipo, Estado, Humedad, Temperatura, Battery, FechaRegistro               | Listado general    |
| `SmartPotDetailsDto`   | Todos los atributos de la entidad + configuración + alertas + historial              | Vista detallada    |
| `HistorialRiegoDto`    | Id, Fecha, VolumenAgua, HumedadInicial, HumedadFinal, Resultado                      | Detalle de riego   |
| `LecturaTelemetriaDto` | Id, Timestamp, Humedad, Ph, Salinidad, Temperatura, ExposicionSolar, HorasExposicion | Medición ambiental |
| `AlertaDto`            | Id, Tipo, ValorDetectado, Urgencia, Recomendacion, GuiaUrl, Fecha                    | Alertas recientes  |

##### Endpoints REST

| Endpoint                           | Método | Acción                            |
| ---------------------------------- | ------ | --------------------------------- |
| `/api/smartpots`                   | GET    | Listar macetas del usuario        |
| `/api/smartpots/{id}`              | GET    | Ver detalles de una maceta        |
| `/api/smartpots`                   | POST   | Registrar maceta nueva (BLE/UUID) |
| `/api/smartpots/{id}`              | PUT    | Editar datos de maceta            |
| `/api/smartpots/{id}`              | DELETE | Eliminar (soft delete)            |
| `/api/smartpots/{id}/water/manual` | POST   | Agregar riego manual              |
| `/api/smartpots/{id}/history`      | GET    | Ver historial de riego            |
| `/api/smartpots/{id}/alerts`       | GET    | Ver alertas activas               |
| `/api/smartpots/{id}/telemetry`    | GET    | Ver telemetría asociada           |

---

### 4.2.3.3. Application Layer

| Comando/Consulta            | Propósito                                 | Entrada                    | Salida                 |
| --------------------------- | ----------------------------------------- | -------------------------- | ---------------------- |
| `RegisterSmartPotCommand`   | Crear maceta vía BLE o UUID               | RegistroDto, userId        | SmartPotDetailsDto     |
| `EditSmartPotCommand`       | Actualizar información general            | potId, EditDto, userId     | SmartPotDetailsDto     |
| `DeleteSmartPotCommand`     | Eliminar (soft delete)                    | potId, userId              | bool                   |
| `RegisterManualWateringCmd` | Agregar evento de riego manual            | potId, Volumen, userId     | HistorialRiegoDto      |
| `GetSmartPotDetailsQuery`   | Consultar todos los detalles de la maceta | potId, userId              | SmartPotDetailsDto     |
| `ListUserSmartPotsQuery`    | Obtener listado resumido                  | userId                     | SmartPotSummaryDto[]   |
| `GetWateringHistoryQuery`   | Ver historial de riegos                   | potId, userId              | HistorialRiegoDto[]    |
| `GetPotAlertsQuery`         | Obtener alertas                           | potId, userId              | AlertaDto[]            |
| `GetPotTelemetryQuery`      | Obtener telemetrías                       | potId, userId, rangoFecha? | LecturaTelemetriaDto[] |

---

### 4.2.3.4. Infrastructure Layer

| Repositorio/Adaptador          | Propósito                               |
| ------------------------------ | --------------------------------------- |
| `ISmartPotRepository`          | Acceso a datos de macetas               |
| `IHistorialRiegoRepository`    | Lectura/escritura de historial de riego |
| `ILecturaTelemetriaRepository` | Persistencia de sensores/telemetría     |
| `IAlertaRepository`            | Manejo de alertas persistentes          |
| `IUsuarioRepository`           | Validación y consulta de usuarios       |

---

#### 4.2.3.5. Bounded Context Software Architecture Component Level Diagrams.

[missing-res]

#### 4.2.3.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.3.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-pot-management/class-diagram-pot-management.png"></image>

##### 4.2.3.6.2. Bounded Context Database Design Diagram.

<image src="../assets/img/capitulo-4/bounded-context-pot-management/database-diagram-pot-management.png"></image>

### 4.2.4. Bounded Context: Plant Management

#### 4.2.4.1. Domain Layer.

## Plant

| Propiedad     | Valor                                                      |
| ------------- | ---------------------------------------------------------- |
| **Nombre**    | Plant                                                      |
| **Categoría** | Aggregate Root                                             |
| **Propósito** | Representar la relación planta–maceta con marcas de tiempo |

### Atributos

| Nombre            | Tipo de dato        | Visibilidad | Descripción                         |
| ----------------- | ------------------- | ----------- | ----------------------------------- |
| id                | `Long`              | private     | Identificador único de la planta    |
| potId             | `Long`              | private     | Identificador de la maceta asociada |
| bestPlantSettings | `BestPlantSettings` | private     | Entorno óptimo para la planta       |
| plantInformation  | `PlantInformation`  | private     | Información de la planta            |
| createdAt         | `DateTime`          | private     | Fecha de creación de la entidad     |
| updatedAt         | `DateTime`          | private     | Fecha de última actualización       |

### Métodos

| Nombre      | Tipo de retorno | Visibilidad | Descripción                                    |
| ----------- | --------------- | ----------- | ---------------------------------------------- |
| changePot   | `void`          | public      | Reasigna a otra maceta y actualiza `updatedAt` |
| markUpdated | `void`          | private     | Actualiza internamente el campo `updatedAt`    |

## BestPlantSettings

| Propiedad     | Valor                                                     |
| ------------- | --------------------------------------------------------- |
| **Nombre**    | BestPlantSettings                                         |
| **Categoría** | Value Object                                              |
| **Propósito** | Representar la información de entorno óptimo de la planta |

### Atributos

| Nombre                 | Tipo de dato | Visibilidad | Descripción                                    |
| ---------------------- | ------------ | ----------- | ---------------------------------------------- |
| humidity               | `Float`      | public      | Nivel de humedad óptimo                        |
| temperature            | `Float`      | public      | Temperatura óptima                             |
| waterIntervalInMinutes | `Int`        | public      | Recomendación de riego por intervalo de tiempo |

## PlantInformation

| Propiedad     | Valor                                   |
| ------------- | --------------------------------------- |
| **Nombre**    | PlantInformation                        |
| **Categoría** | Value Object                            |
| **Propósito** | Representar la información de la planta |

### Atributos

| Nombre      | Tipo de dato | Visibilidad | Descripción                     |
| ----------- | ------------ | ----------- | ------------------------------- |
| name        | `String`     | public      | Nombre de la planta             |
| description | `String`     | public      | Descripción de la planta        |
| imageUrl    | `String`     | public      | Imagen referencial de la planta |
| family      | `String`     | public      | Familia de la planta            |
| genus       | `String`     | public      | Género de la planta             |
| species     | `String`     | public      | Especie de la planta            |

## PlantFactory

| Propiedad     | Valor                                  |
| ------------- | -------------------------------------- |
| **Nombre**    | PlantFactory                           |
| **Categoría** | Factory                                |
| **Propósito** | Construir nuevas instancias de `Plant` |

### Métodos

| Nombre | Tipo de retorno | Visibilidad | Descripción                                                        |
| ------ | --------------- | ----------- | ------------------------------------------------------------------ |
| create | `Plant`         | public      | Crea un `Plant` dado `potId`, inicializa `createdAt` y `updatedAt` |

## IPlantRepository

| Propiedad     | Valor                                   |
| ------------- | --------------------------------------- |
| **Nombre**    | IPlantRepository                        |
| **Categoría** | Repository                              |
| **Propósito** | Persistir y recuperar entidades `Plant` |

### Métodos

| Nombre   | Tipo de retorno | Visibilidad | Descripción                    |
| -------- | --------------- | ----------- | ------------------------------ |
| findById | `Plant?`        | public      | Busca una planta por su ID     |
| create   | `Unit`          | public      | Persiste una nueva planta      |
| update   | `Unit`          | public      | Actualiza una planta existente |
| delete   | `Unit`          | public      | Elimina una planta por su ID   |

## IPlantRecommendationService

| Propiedad     | Valor                                               |
| ------------- | --------------------------------------------------- |
| **Nombre**    | IPlantRecommendationService                         |
| **Categoría** | Domain Service                                      |
| **Propósito** | Proveer la mejor configuración para una planta dada |

### Métodos

| Nombre               | Tipo de retorno | Visibilidad | Descripción                            |
| -------------------- | --------------- | ----------- | -------------------------------------- |
| getBestPlantSettings | `String?`       | public      | Retorna ajustes óptimos para la planta |

## PlantRecommendationService

| Propiedad     | Valor                                                   |
| ------------- | ------------------------------------------------------- |
| **Nombre**    | PlantRecommendationService                              |
| **Categoría** | Domain Service Implementation                           |
| **Propósito** | Implementar la lógica de recomendación de configuración |

#### 4.2.4.2. Interface Layer.

## PlantController

| Propiedad     | Valor                                          |
| ------------- | ---------------------------------------------- |
| **Nombre**    | PlantController                                |
| **Categoría** | Controller                                     |
| **Propósito** | Exponer endpoints REST para gestión de plantas |
| **Ruta**      | `/api/plant/`                                  |

## Métodos

| Nombre      | Ruta            | Acción                         | Handle               |
| ----------- | --------------- | ------------------------------ | -------------------- |
| getPlant    | `/{id:long}`    | Obtener detalles de una planta | `GetPlantQuery`      |
| createPlant | `/create`       | Crear nueva planta             | `CreatePlantCommand` |
| updatePlant | `/update`       | Actualizar planta existente    | `UpdatePlantCommand` |
| deletePlant | `/delete-plant` | Eliminar planta por su ID      | `DeletePlantCommand` |

#### 4.2.4.3. Application Layer.

## GetPlantQueryHandler

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | GetPlantQueryHandler                       |
| **Categoría** | Query Handler                              |
| **Propósito** | Manejar la consulta de obtención de planta |

## CreatePlantCommandHandler

| Propiedad     | Valor                                 |
| ------------- | ------------------------------------- |
| **Nombre**    | CreatePlantCommandHandler             |
| **Categoría** | Command Handler                       |
| **Propósito** | Ejecutar lógica de creación de planta |

## UpdatePlantCommandHandler

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | UpdatePlantCommandHandler                  |
| **Categoría** | Command Handler                            |
| **Propósito** | Ejecutar lógica de actualización de planta |

## DeletePlantCommandHandler

| Propiedad     | Valor                                    |
| ------------- | ---------------------------------------- |
| **Nombre**    | DeletePlantCommandHandler                |
| **Categoría** | Command Handler                          |
| **Propósito** | Ejecutar lógica de eliminación de planta |

## PlantCreatedEventHandler

| Propiedad     | Valor                                 |
| ------------- | ------------------------------------- |
| **Nombre**    | PlantCreatedEventHandler              |
| **Categoría** | Event Handler                         |
| **Propósito** | Reaccionar al evento de planta creada |

## PlantUpdatedEventHandler

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | PlantUpdatedEventHandler                   |
| **Categoría** | Event Handler                              |
| **Propósito** | Reaccionar al evento de planta actualizada |

## PlantDeletedEventHandler

| Propiedad     | Valor                                    |
| ------------- | ---------------------------------------- |
| **Nombre**    | PlantDeletedEventHandler                 |
| **Categoría** | Event Handler                            |
| **Propósito** | Reaccionar al evento de planta eliminada |

## IPlantInfoProvider

| Propiedad     | Valor                                                        |
| ------------- | ------------------------------------------------------------ |
| **Nombre**    | IPlantInfoProvider                                           |
| **Categoría** | Interface (Application Service)                              |
| **Propósito** | Obtener especificaciones de planta desde un servicio externo |

#### 4.2.4.4. Infrastructure Layer.

## PlantRepository

| Propiedad     | Valor                                  |
| ------------- | -------------------------------------- |
| **Nombre**    | PlantRepository                        |
| **Categoría** | Repository Implementation              |
| **Propósito** | Implementar `IPlantRepository` con ORM |

### Métodos

| Nombre        | Tipo de retorno | Visibilidad | Descripción                 |
| ------------- | --------------- | ----------- | --------------------------- |
| findById      | `Plant?`        | public      | Busca planta por su ID      |
| findByPotId   | `List<Plant>`   | public      | Lista plantas de una maceta |
| findByUserUid | `List<Plant>`   | public      | Lista plantas de un usuario |
| create        | `Unit`          | public      | Persiste nueva planta       |
| update        | `Unit`          | public      | Actualiza planta existente  |
| delete        | `Unit`          | public      | Elimina planta por ID       |

## PlantInfoProvider

| Propiedad     | Valor                                                         |
| ------------- | ------------------------------------------------------------- |
| **Nombre**    | PlantInfoProvider                                             |
| **Categoría** | External Service Implementation                               |
| **Propósito** | Implementar `IPlantInfoProvider` para obtener specs de planta |

#### 4.2.4.5. Bounded Context Software Architecture Component Level Diagrams.

[missing-res]

#### 4.2.4.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.4.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-plant-management/class-diagram-plant-management.png"></image>

##### 4.2.4.6.2. Bounded Context Database Design Diagram.

<image src="../assets/img/capitulo-4/bounded-context-plant-management/database-diagram-plant-management.png"></image>

### 4.2.5. Bounded Context: System Monitoring & Control

#### 4.2.5.1. Domain Layer.

## Alert

| Propiedad     | Valor                                                              |
| ------------- | ------------------------------------------------------------------ |
| **Nombre**    | Alert                                                              |
| **Categoría** | Aggregate Root                                                     |
| **Propósito** | Representar una alerta crítica generada por sensores de una maceta |

### Atributos

| Nombre   | Tipo de dato   | Visibilidad | Descripción                                        |
| -------- | -------------- | ----------- | -------------------------------------------------- |
| id       | `Long`         | private     | Identificador único de la alerta                   |
| potId    | `Long`         | private     | UID de la maceta asociada                          |
| content  | `AlertContent` | private     | Detalles de lecturas de sensores y dispositivo IoT |
| issuedAt | `DateTime`     | private     | Fecha y hora de emisión de la alerta               |
| resolved | `Boolean`      | private     | Indica si la alerta ha sido resuelta               |

### Métodos

| Nombre        | Tipo de retorno | Visibilidad | Descripción                               |
| ------------- | --------------- | ----------- | ----------------------------------------- |
| markResolved  | `void`          | public      | Marca la alerta como resuelta             |
| updateContent | `void`          | public      | Reemplaza el `content` y actualiza estado |

## AlertContent

| Propiedad     | Valor                                                         |
| ------------- | ------------------------------------------------------------- |
| **Nombre**    | AlertContent                                                  |
| **Categoría** | Value Object                                                  |
| **Propósito** | Agrupar las lecturas de sensores y estado del dispositivo IoT |

### Atributos

| Nombre      | Tipo de dato     | Visibilidad | Descripción                                      |
| ----------- | ---------------- | ----------- | ------------------------------------------------ |
| humidity    | `SensorAlert`    | private     | Lectura y estado del sensor de humedad           |
| temperature | `SensorAlert`    | private     | Lectura y estado del sensor de temperatura       |
| water       | `SensorAlert`    | private     | Lectura y estado del sensor de nivel de agua     |
| iotDevice   | `IotDeviceAlert` | private     | Estado del dispositivo IoT (por ejemplo batería) |

## SensorAlert

| Propiedad     | Valor                                                  |
| ------------- | ------------------------------------------------------ |
| **Nombre**    | SensorAlert                                            |
| **Categoría** | Value Object                                           |
| **Propósito** | Encapsular una medición de sensor y su nivel de alerta |

### Atributos

| Nombre | Tipo de dato   | Visibilidad | Descripción                               |
| ------ | -------------- | ----------- | ----------------------------------------- |
| value  | `Float`        | private     | Valor de la medición                      |
| status | `SensorStatus` | private     | Nivel de alerta (`Low`, `Normal`, `High`) |

### Métodos

| Nombre     | Tipo de retorno | Visibilidad | Descripción                                   |
| ---------- | --------------- | ----------- | --------------------------------------------- |
| isCritical | `Boolean`       | public      | Devuelve `true` si `status` es `Low` o `High` |

## SensorStatus

| Propiedad     | Valor                                  |
| ------------- | -------------------------------------- |
| **Nombre**    | SensorStatus                           |
| **Categoría** | Enum                                   |
| **Propósito** | Definir los posibles estados de alerta |

### Valores

| Valor  | Descripción                       |
| ------ | --------------------------------- |
| Low    | Nivel por debajo del rango normal |
| Normal | Dentro del rango esperado         |
| High   | Nivel por encima del rango normal |

## IotDeviceAlert

| Propiedad     | Valor                                                            |
| ------------- | ---------------------------------------------------------------- |
| **Nombre**    | IotDeviceAlert                                                   |
| **Categoría** | Value Object                                                     |
| **Propósito** | Representar el estado de un dispositivo IoT asociado a la maceta |

### Atributos

| Nombre       | Tipo de dato | Visibilidad | Descripción                                    |
| ------------ | ------------ | ----------- | ---------------------------------------------- |
| batteryLevel | `Float`      | private     | Porcentaje de batería restante del dispositivo |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                                     |
| ------------ | --------------- | ----------- | ----------------------------------------------- |
| isBatteryLow | `Boolean`       | public      | `true` si `batteryLevel` está por debajo de 15% |

## IAlertRepository

| Propiedad     | Valor                                   |
| ------------- | --------------------------------------- |
| **Nombre**    | IAlertRepository                        |
| **Categoría** | Repository                              |
| **Propósito** | Persistir y recuperar entidades `Alert` |

### Métodos

| Nombre   | Tipo de retorno | Visibilidad | Descripción                    |
| -------- | --------------- | ----------- | ------------------------------ |
| findById | `Alert?`        | public      | Recupera una alerta por su ID  |
| create   | `Unit`          | public      | Persiste una nueva alerta      |
| update   | `Unit`          | public      | Actualiza una alerta existente |
| delete   | `Unit`          | public      | Elimina una alerta por su ID   |

## AlertFactory

| Propiedad     | Valor                               |
| ------------- | ----------------------------------- |
| **Nombre**    | AlertFactory                        |
| **Categoría** | Factory                             |
| **Propósito** | Crear instancias válidas de `Alert` |

### Métodos

| Nombre | Tipo de retorno | Visibilidad | Descripción                                        |
| ------ | --------------- | ----------- | -------------------------------------------------- |
| create | `Alert`         | public      | Construye un `Alert` dado `potId` y `AlertContent` |

## IAlertReportNotePolicy

| Propiedad     | Valor                                                   |
| ------------- | ------------------------------------------------------- |
| **Nombre**    | IAlertReportNotePolicy                                  |
| **Categoría** | Domain Service                                          |
| **Propósito** | Generar una nota contextual para un conjunto de alertas |

### Métodos

| Nombre  | Tipo de retorno | Visibilidad | Descripción                                         |
| ------- | --------------- | ----------- | --------------------------------------------------- |
| noteFor | `String?`       | public      | Devuelve texto explicativo para la lista de alertas |

## AlertReportNotePolicy

| Propiedad     | Valor                                                      |
| ------------- | ---------------------------------------------------------- |
| **Nombre**    | AlertReportNotePolicy                                      |
| **Categoría** | Domain Service Implementation                              |
| **Propósito** | Implementar la lógica de generación de notas para reportes |

#### 4.2.5.2. Interface Layer.

## AlertController

| Propiedad     | Valor                                          |
| ------------- | ---------------------------------------------- |
| **Nombre**    | AlertController                                |
| **Categoría** | Controller                                     |
| **Propósito** | Exponer endpoints REST para gestión de alertas |
| **Ruta**      | `/api/alerts/`                                 |

### Métodos

| Nombre      | Ruta               | Acción                              | Handle                |
| ----------- | ------------------ | ----------------------------------- | --------------------- |
| getAlert    | `/{id:long}`       | Obtener alerta por ID               | `GetAlertQuery`       |
| createAlert | `/create`          | Crear nueva alerta                  | `CreateAlertCommand`  |
| updateAlert | `/resolved`        | Marcar alerta como resuelta         | `UpdateAlertCommand`  |
| updateAlert | `/generate-report` | Genera un reporte en base a alertas | `CreateReportCommand` |

#### 4.2.5.3. Application Layer.

## GetAlertQueryHandler

| Propiedad     | Valor                               |
| ------------- | ----------------------------------- |
| **Nombre**    | GetAlertQueryHandler                |
| **Categoría** | Query Handler                       |
| **Propósito** | Manejar la consulta `GetAlertQuery` |

## CreateAlertCommandHandler

| Propiedad     | Valor                         |
| ------------- | ----------------------------- |
| **Nombre**    | CreateAlertCommandHandler     |
| **Categoría** | Command Handler               |
| **Propósito** | Ejecutar `CreateAlertCommand` |

## UpdateAlertCommandHandler

| Propiedad     | Valor                         |
| ------------- | ----------------------------- |
| **Nombre**    | UpdateAlertCommandHandler     |
| **Categoría** | Command Handler               |
| **Propósito** | Ejecutar `UpdateAlertCommand` |

## CreateReportCommandHandler

| Propiedad     | Valor                          |
| ------------- | ------------------------------ |
| **Nombre**    | CreateReportCommandHandler     |
| **Categoría** | Command Handler                |
| **Propósito** | Ejecutar `CreateReportCommand` |

## AlertCreatedEventHandler

| Propiedad     | Valor                                  |
| ------------- | -------------------------------------- |
| **Nombre**    | AlertCreatedEventHandler               |
| **Categoría** | Event Handler                          |
| **Propósito** | Reaccionar tras creación de una alerta |

## AlertUpdatedEventHandler

| Propiedad     | Valor                                |
| ------------- | ------------------------------------ |
| **Nombre**    | AlertUpdatedEventHandler             |
| **Categoría** | Event Handler                        |
| **Propósito** | Reaccionar tras resolución de alerta |

## IAlertService

| Propiedad     | Valor                                              |
| ------------- | -------------------------------------------------- |
| **Nombre**    | IAlertService                                      |
| **Categoría** | Application Service                                |
| **Propósito** | Definir acciones de notificación según tipo alerta |

### Métodos

| Nombre            | Tipo de retorno | Visibilidad | Descripción                                        |
| ----------------- | --------------- | ----------- | -------------------------------------------------- |
| lowBatteryAlert   | `Unit`          | public      | Lógica para alertas de batería baja                |
| disconnectedAlert | `Unit`          | public      | Lógica para alertas de desconexión del dispositivo |

## AlertService

| Propiedad     | Valor                              |
| ------------- | ---------------------------------- |
| **Nombre**    | AlertService                       |
| **Categoría** | Application Service Implementation |
| **Propósito** | Implementar `IAlertService`        |

## IAlertReportGenerationService

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | IAlertReportGenerationService             |
| **Categoría** | Application Service                       |
| **Propósito** | Definir generación de reportes de alertas |

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                       |
| -------------- | --------------- | ----------- | ------------------------------------------------- |
| generateReport | `String?`       | public      | Compila y devuelve un reporte a partir de alertas |

## IEmailService

| Propiedad     | Valor                    |
| ------------- | ------------------------ |
| **Nombre**    | IEmailService            |
| **Categoría** | Application Service      |
| **Propósito** | Definir envío de correos |

### Métodos

| Nombre    | Tipo de retorno | Visibilidad | Descripción                         |
| --------- | --------------- | ----------- | ----------------------------------- |
| sendEmail | `Unit`          | public      | Envía un correo con asunto y cuerpo |

#### 4.2.5.4. Infrastructure Layer.

## AlertReportGenerationService

| Propiedad     | Valor                                       |
| ------------- | ------------------------------------------- |
| **Nombre**    | AlertReportGenerationService                |
| **Categoría** | Service Implementation                      |
| **Propósito** | Implementar `IAlertReportGenerationService` |

## SendGridService

| Propiedad     | Valor                                       |
| ------------- | ------------------------------------------- |
| **Nombre**    | SendGridService                             |
| **Categoría** | Service Implementation                      |
| **Propósito** | Implementar `IEmailService` usando SendGrid |

## AlertRepository

| Propiedad     | Valor                                                 |
| ------------- | ----------------------------------------------------- |
| **Nombre**    | AlertRepository                                       |
| **Categoría** | Repository Implementation                             |
| **Propósito** | Implementar `IAlertRepository` con persistencia en BD |

#### 4.2.5.5. Bounded Context Software Architecture Component Level Diagrams.

[missing-res]

#### 4.2.5.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.5.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-system-monitoring-and-control/class-diagram-system-monitoring-and-control.png"></image>

##### 4.2.5.6.2. Bounded Context Database Design Diagram.

<image src="../assets/img/capitulo-4/bounded-context-system-monitoring-and-control/database-diagram-system-monitoring-and-control.png"></image>

### 4.2.6. Bounded Context: Watering Management

#### 4.2.6.1. Domain Layer.

## WateringSchedule

| Propiedad     | Valor                                                            |
| ------------- | ---------------------------------------------------------------- |
| **Nombre**    | WateringSchedule                                                 |
| **Categoría** | Aggregate Root                                                   |
| **Propósito** | Representar una programación de riego para una maceta específica |

### Atributos

| Nombre    | Tipo de dato | Visibilidad | Descripción                                 |
| --------- | ------------ | ----------- | ------------------------------------------- |
| potId     | `Long`       | private     | Identificador de la maceta                  |
| startTime | `DateTime`   | private     | Hora de inicio del riego                    |
| frequency | `String`     | private     | Frecuencia (diaria, semanal, personalizada) |
| duration  | `Int`        | private     | Duración en minutos                         |
| isActive  | `Boolean`    | private     | Si la programación está activa o suspendida |
| createdAt | `DateTime`   | private     | Fecha de creación                           |
| updatedAt | `DateTime`   | private     | Última fecha de actualización               |

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                 |
| -------------- | --------------- | ----------- | ------------------------------------------- |
| updateSchedule | `void`          | public      | Modifica horario, frecuencia o duración     |
| activate       | `void`          | public      | Activa la programación                      |
| deactivate     | `void`          | public      | Suspende la programación                    |
| markUpdated    | `void`          | private     | Actualiza internamente el campo `updatedAt` |

## WateringLog

| Propiedad     | Valor                                          |
| ------------- | ---------------------------------------------- |
| **Nombre**    | WateringLog                                    |
| **Categoría** | Entity                                         |
| **Propósito** | Registrar una ejecución de riego en una maceta |

### Atributos

| Nombre    | Tipo de dato | Visibilidad | Descripción                             |
| --------- | ------------ | ----------- | --------------------------------------- |
| id        | `Long`       | private     | Identificador del log                   |
| potId     | `Long`       | private     | Identificador de la maceta              |
| timestamp | `DateTime`   | private     | Momento de ejecución                    |
| status    | `String`     | private     | Estado del riego (exitoso, error, etc.) |

## IWateringScheduleRepository

| Propiedad     | Valor                                        |
| ------------- | -------------------------------------------- |
| **Nombre**    | IWateringScheduleRepository                  |
| **Categoría** | Repository                                   |
| **Propósito** | Gestionar persistencia de `WateringSchedule` |

### Métodos

| Nombre      | Tipo de retorno     | Descripción                           |
| ----------- | ------------------- | ------------------------------------- |
| findByPotId | `WateringSchedule?` | Obtener programación de riego         |
| create      | `Unit`              | Guardar nueva programación            |
| update      | `Unit`              | Actualizar una programación existente |
| delete      | `Unit`              | Eliminar programación por `potId`     |

## IWateringLogRepository

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | IWateringLogRepository                    |
| **Categoría** | Repository                                |
| **Propósito** | Gestionar registros de ejecución de riego |

### Métodos

| Nombre      | Tipo de retorno     | Descripción                       |
| ----------- | ------------------- | --------------------------------- |
| create      | `Unit`              | Almacenar un nuevo `WateringLog`  |
| findByPotId | `List<WateringLog>` | Consultar registros de una maceta |

---

#### 4.2.6.2. Interface Layer.

## WateringScheduleController

| Propiedad     | Valor                                                              |
| ------------- | ------------------------------------------------------------------ |
| **Nombre**    | WateringScheduleController                                         |
| **Categoría** | Controller                                                         |
| **Propósito** | Exponer los servicios REST para gestionar la programación de riego |
| **Ruta**      | `/api/watering-schedules/`                                         |

### Métodos

| Nombre             | Ruta          | Acción                             | Handle                              |
| ------------------ | ------------- | ---------------------------------- | ----------------------------------- |
| getSchedule        | `/{id:long}`  | Obtener programación de riego      | `GetWateringScheduleQuery`          |
| createSchedule     | `/create`     | Crear nueva programación de riego  | `CreateWateringScheduleCommand`     |
| updateSchedule     | `/update`     | Actualizar programación existente  | `UpdateWateringScheduleCommand`     |
| deactivateSchedule | `/deactivate` | Suspender la programación de riego | `DeactivateWateringScheduleCommand` |
| activateSchedule   | `/activate`   | Activar la programación de riego   | `ActivateWateringScheduleCommand`   |

## WateringLogController

| Propiedad     | Valor                                                       |
| ------------- | ----------------------------------------------------------- |
| **Nombre**    | WateringLogController                                       |
| **Categoría** | Controller                                                  |
| **Propósito** | Exponer los servicios REST para consultar los logs de riego |
| **Ruta**      | `/api/watering-logs/`                                       |

### Métodos

| Nombre       | Ruta                | Acción                              | Handle                      |
| ------------ | ------------------- | ----------------------------------- | --------------------------- |
| getLog       | `/{id:long}`        | Obtener log de riego por ID         | `GetWateringLogQuery`       |
| getLogsByPot | `/pot/{potId:long}` | Obtener logs de riego de una maceta | `GetWateringLogsByPotQuery` |

---

#### 4.2.6.3. Application Layer.

## GetWateringScheduleQueryHandler

| Propiedad     | Valor                                                             |
| ------------- | ----------------------------------------------------------------- |
| **Nombre**    | GetWateringScheduleQueryHandler                                   |
| **Categoría** | Query Handler                                                     |
| **Propósito** | Manejar la consulta para obtener una programación de riego por ID |

## CreateWateringScheduleCommandHandler

| Propiedad     | Valor                                                  |
| ------------- | ------------------------------------------------------ |
| **Nombre**    | CreateWateringScheduleCommandHandler                   |
| **Categoría** | Command Handler                                        |
| **Propósito** | Manejar la creación de una nueva programación de riego |

## UpdateWateringScheduleCommandHandler

| Propiedad     | Valor                                                           |
| ------------- | --------------------------------------------------------------- |
| **Nombre**    | UpdateWateringScheduleCommandHandler                            |
| **Categoría** | Command Handler                                                 |
| **Propósito** | Manejar la actualización de una programación de riego existente |

## DeactivateWateringScheduleCommandHandler

| Propiedad     | Valor                                                 |
| ------------- | ----------------------------------------------------- |
| **Nombre**    | DeactivateWateringScheduleCommandHandler              |
| **Categoría** | Command Handler                                       |
| **Propósito** | Manejar la desactivación de una programación de riego |

## ActivateWateringScheduleCommandHandler

| Propiedad     | Valor                                              |
| ------------- | -------------------------------------------------- |
| **Nombre**    | ActivateWateringScheduleCommandHandler             |
| **Categoría** | Command Handler                                    |
| **Propósito** | Manejar la activación de una programación de riego |

## GetWateringLogQueryHandler

| Propiedad     | Valor                                       |
| ------------- | ------------------------------------------- |
| **Nombre**    | GetWateringLogQueryHandler                  |
| **Categoría** | Query Handler                               |
| **Propósito** | Manejar la consulta de logs de riego por ID |

## GetWateringLogsByPotQueryHandler

| Propiedad     | Valor                                                   |
| ------------- | ------------------------------------------------------- |
| **Nombre**    | GetWateringLogsByPotQueryHandler                        |
| **Categoría** | Query Handler                                           |
| **Propósito** | Manejar la consulta de logs de riego por potId (maceta) |

---

#### 4.2.6.4. Infrastructure Layer.

## WateringScheduleRepository

| Propiedad     | Valor                                                                         |
| ------------- | ----------------------------------------------------------------------------- |
| **Nombre**    | WateringScheduleRepository                                                    |
| **Categoría** | Repository Implementation                                                     |
| **Propósito** | Implementar `IWateringScheduleRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre      | Tipo de retorno     | Visibilidad | Descripción                                    |
| ----------- | ------------------- | ----------- | ---------------------------------------------- |
| findByPotId | `WateringSchedule?` | public      | Buscar programación de riego por `potId`       |
| create      | `Unit`              | public      | Persistir una nueva programación de riego      |
| update      | `Unit`              | public      | Actualizar una programación de riego existente |
| delete      | `Unit`              | public      | Eliminar programación de riego por `potId`     |

## WateringLogRepository

| Propiedad     | Valor                                                                    |
| ------------- | ------------------------------------------------------------------------ |
| **Nombre**    | WateringLogRepository                                                    |
| **Categoría** | Repository Implementation                                                |
| **Propósito** | Implementar `IWateringLogRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre      | Tipo de retorno     | Visibilidad | Descripción                         |
| ----------- | ------------------- | ----------- | ----------------------------------- |
| create      | `Unit`              | public      | Persistir un nuevo log de riego     |
| findByPotId | `List<WateringLog>` | public      | Recuperar logs de riego por `potId` |

---

#### 4.2.6.5. Bounded Context Software Architecture Component Level Diagrams.

#### 4.2.6.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.6.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-watering-management/WateringScheduleClassDiagram.png"></image>

##### 4.2.6.6.2. Bounded Context Database Design Diagram.

<image src="../assets/img/capitulo-4/bounded-context-watering-management/WateringManagementDbDiagram.png"></image>

### 4.2.7. Bounded Context: Subscriptions & Payments

#### 4.2.7.1. Domain Layer.

## Subscription

| Propiedad     | Valor                                              |
| ------------- | -------------------------------------------------- |
| **Nombre**    | Subscription                                       |
| **Categoría** | Aggregate Root                                     |
| **Propósito** | Representar una suscripción activa para un usuario |

### Atributos

| Nombre    | Tipo de dato | Visibilidad | Descripción                                  |
| --------- | ------------ | ----------- | -------------------------------------------- |
| userId    | `Long`       | private     | Identificador único del usuario              |
| planId    | `Long`       | private     | Identificador del plan de suscripción        |
| status    | `String`     | private     | Estado de la suscripción (activa, cancelada) |
| startDate | `DateTime`   | private     | Fecha de inicio de la suscripción            |
| endDate   | `DateTime`   | private     | Fecha de expiración de la suscripción        |
| createdAt | `DateTime`   | private     | Fecha de creación de la suscripción          |
| updatedAt | `DateTime`   | private     | Fecha de última actualización                |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                                 |
| ------------ | --------------- | ----------- | ------------------------------------------- |
| activate     | `void`          | public      | Activa la suscripción                       |
| cancel       | `void`          | public      | Cancela la suscripción                      |
| updateStatus | `void`          | public      | Actualiza el estado de la suscripción       |
| markUpdated  | `void`          | private     | Actualiza internamente el campo `updatedAt` |

## SubscriptionPlan

| Propiedad     | Valor                                                         |
| ------------- | ------------------------------------------------------------- |
| **Nombre**    | SubscriptionPlan                                              |
| **Categoría** | Value Object                                                  |
| **Propósito** | Representar los detalles de un plan de suscripción disponible |

### Atributos

| Nombre    | Tipo de dato   | Visibilidad | Descripción                              |
| --------- | -------------- | ----------- | ---------------------------------------- |
| name      | `String`       | public      | Nombre del plan (p.ej., Básico, Premium) |
| price     | `Decimal`      | public      | Precio mensual del plan                  |
| duration  | `Int`          | public      | Duración del plan en meses               |
| features  | `List<String>` | public      | Características que ofrece el plan       |
| createdAt | `DateTime`     | private     | Fecha de creación del plan               |

## PaymentTransaction

| Propiedad     | Valor                                                                  |
| ------------- | ---------------------------------------------------------------------- |
| **Nombre**    | PaymentTransaction                                                     |
| **Categoría** | Entity                                                                 |
| **Propósito** | Representar los pagos realizados por un usuario para sus suscripciones |

### Atributos

| Nombre         | Tipo de dato | Visibilidad | Descripción                                    |
| -------------- | ------------ | ----------- | ---------------------------------------------- |
| transactionId  | `String`     | private     | Identificador único de la transacción          |
| subscriptionId | `Long`       | private     | Identificador de la suscripción                |
| amount         | `Decimal`    | private     | Monto de la transacción                        |
| status         | `String`     | private     | Estado de la transacción (completada, fallida) |
| createdAt      | `DateTime`   | private     | Fecha de la transacción                        |

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                 |
| -------------- | --------------- | ----------- | ------------------------------------------- |
| processPayment | `void`          | public      | Procesa el pago para una suscripción        |
| updateStatus   | `void`          | public      | Actualiza el estado de la transacción       |
| markUpdated    | `void`          | private     | Actualiza internamente el campo `updatedAt` |

## ISubscriptionRepository

| Propiedad     | Valor                                          |
| ------------- | ---------------------------------------------- |
| **Nombre**    | ISubscriptionRepository                        |
| **Categoría** | Repository                                     |
| **Propósito** | Persistir y recuperar entidades `Subscription` |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                                  |
| ------------ | --------------- | ----------- | -------------------------------------------- |
| findByUserId | `Subscription?` | public      | Recupera la suscripción activa de un usuario |
| create       | `Unit`          | public      | Crea una nueva suscripción                   |
| update       | `Unit`          | public      | Actualiza una suscripción existente          |
| delete       | `Unit`          | public      | Elimina una suscripción por `userId`         |

## IPaymentTransactionRepository

| Propiedad     | Valor                                       |
| ------------- | ------------------------------------------- |
| **Nombre**    | IPaymentTransactionRepository               |
| **Categoría** | Repository                                  |
| **Propósito** | Persistir y recuperar transacciones de pago |

### Métodos

| Nombre   | Tipo de retorno       | Visibilidad | Descripción                                  |
| -------- | --------------------- | ----------- | -------------------------------------------- |
| create   | `Unit`                | public      | Crea una nueva transacción de pago           |
| findById | `PaymentTransaction?` | public      | Recupera una transacción por `transactionId` |
| update   | `Unit`                | public      | Actualiza una transacción existente          |
| delete   | `Unit`                | public      | Elimina una transacción                      |

---

#### 4.2.7.2. Interface Layer.

## SubscriptionController

| Propiedad     | Valor                                                              |
| ------------- | ------------------------------------------------------------------ |
| **Nombre**    | SubscriptionController                                             |
| **Categoría** | Controller                                                         |
| **Propósito** | Exponer los servicios REST para gestionar suscripciones de usuario |
| **Ruta**      | `/api/subscriptions/`                                              |

### Métodos

| Nombre             | Ruta             | Acción                               | Handle                      |
| ------------------ | ---------------- | ------------------------------------ | --------------------------- |
| getSubscription    | `/{userId:long}` | Obtener la suscripción de un usuario | `GetSubscriptionQuery`      |
| createSubscription | `/create`        | Crear nueva suscripción              | `CreateSubscriptionCommand` |
| updateSubscription | `/update`        | Actualizar suscripción               | `UpdateSubscriptionCommand` |
| cancelSubscription | `/cancel`        | Cancelar suscripción                 | `CancelSubscriptionCommand` |

## PaymentTransactionController

| Propiedad     | Valor                                                           |
| ------------- | --------------------------------------------------------------- |
| **Nombre**    | PaymentTransactionController                                    |
| **Categoría** | Controller                                                      |
| **Propósito** | Exponer los servicios REST para gestionar transacciones de pago |
| **Ruta**      | `/api/payment-transactions/`                                    |

### Métodos

| Nombre            | Ruta                    | Acción                                        | Handle                            |
| ----------------- | ----------------------- | --------------------------------------------- | --------------------------------- |
| getPayment        | `/{transactionId:long}` | Obtener transacción por ID                    | `GetPaymentTransactionQuery`      |
| createPayment     | `/create`               | Crear una nueva transacción                   | `CreatePaymentTransactionCommand` |
| updatePayment     | `/update`               | Actualizar estado de la transacción           | `UpdatePaymentTransactionCommand` |
| getPaymentsByUser | `/user/{userId:long}`   | Obtener todas las transacciones de un usuario | `GetPaymentsByUserQuery`          |

---

#### 4.2.7.3. Application Layer.

## GetSubscriptionQueryHandler

| Propiedad     | Valor                                                         |
| ------------- | ------------------------------------------------------------- |
| **Nombre**    | GetSubscriptionQueryHandler                                   |
| **Categoría** | Query Handler                                                 |
| **Propósito** | Manejar la consulta para obtener una suscripción por `userId` |

## CreateSubscriptionCommandHandler

| Propiedad     | Valor                                        |
| ------------- | -------------------------------------------- |
| **Nombre**    | CreateSubscriptionCommandHandler             |
| **Categoría** | Command Handler                              |
| **Propósito** | Manejar la creación de una nueva suscripción |

## UpdateSubscriptionCommandHandler

| Propiedad     | Valor                                                 |
| ------------- | ----------------------------------------------------- |
| **Nombre**    | UpdateSubscriptionCommandHandler                      |
| **Categoría** | Command Handler                                       |
| **Propósito** | Manejar la actualización de una suscripción existente |

## CancelSubscriptionCommandHandler

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | CancelSubscriptionCommandHandler          |
| **Categoría** | Command Handler                           |
| **Propósito** | Manejar la cancelación de una suscripción |

## GetPaymentTransactionQueryHandler

| Propiedad     | Valor                                                    |
| ------------- | -------------------------------------------------------- |
| **Nombre**    | GetPaymentTransactionQueryHandler                        |
| **Categoría** | Query Handler                                            |
| **Propósito** | Manejar la consulta para obtener una transacción de pago |

## GetPaymentsByUserQueryHandler

| Propiedad     | Valor                                                            |
| ------------- | ---------------------------------------------------------------- |
| **Nombre**    | GetPaymentsByUserQueryHandler                                    |
| **Categoría** | Query Handler                                                    |
| **Propósito** | Manejar la consulta para obtener las transacciones de un usuario |

---

#### 4.2.7.4. Infrastructure Layer.

## SubscriptionRepository

| Propiedad     | Valor                                                                     |
| ------------- | ------------------------------------------------------------------------- |
| **Nombre**    | SubscriptionRepository                                                    |
| **Categoría** | Repository Implementation                                                 |
| **Propósito** | Implementar `ISubscriptionRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                           |
| ------------ | --------------- | ----------- | ------------------------------------- |
| findByUserId | `Subscription?` | public      | Recupera la suscripción de un usuario |
| create       | `Unit`          | public      | Persistir una nueva suscripción       |
| update       | `Unit`          | public      | Actualiza una suscripción existente   |
| delete       | `Unit`          | public      | Elimina la suscripción por `userId`   |

## PaymentTransactionRepository

| Propiedad     | Valor                                                                           |
| ------------- | ------------------------------------------------------------------------------- |
| **Nombre**    | PaymentTransactionRepository                                                    |
| **Categoría** | Repository Implementation                                                       |
| **Propósito** | Implementar `IPaymentTransactionRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre   | Tipo de retorno       | Visibilidad | Descripción                                  |
| -------- | --------------------- | ----------- | -------------------------------------------- |
| create   | `Unit`                | public      | Persistir una nueva transacción de pago      |
| findById | `PaymentTransaction?` | public      | Recupera una transacción por `transactionId` |
| update   | `Unit`                | public      | Actualiza una transacción existente          |
| delete   | `Unit`                | public      | Elimina una transacción                      |

---

#### 4.2.7.5. Bounded Context Software Architecture Component Level Diagrams.

#### 4.2.7.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.7.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-subscriptions-and-payments/Subscription&PaymentsClassDiagram.png"></image>

##### 4.2.7.6.2. Bounded Context Database Design Diagram.

<image src="../assets/img/capitulo-4/bounded-context-subscriptions-and-payments/Subscriptions&PaymentsDbDiagram.png"></image>

### 4.2.8. Bounded Context: Caring Intelligence

#### 4.2.8.1. Domain Layer.

## Recommendation

| Propiedad     | Valor                                                             |
| ------------- | ----------------------------------------------------------------- |
| **Nombre**    | Recommendation                                                    |
| **Categoría** | Aggregate Root                                                    |
| **Propósito** | Generar recomendaciones personalizadas para el cuidado de plantas |

### Atributos

| Nombre             | Tipo de dato | Visibilidad | Descripción                                       |
| ------------------ | ------------ | ----------- | ------------------------------------------------- |
| plantId            | `Long`       | private     | Identificador de la planta                        |
| userId             | `Long`       | private     | Identificador del usuario                         |
| recommendationType | `String`     | private     | Tipo de recomendación (riego, luz, fertilización) |
| value              | `String`     | private     | Valor o mensaje de la recomendación               |
| createdAt          | `DateTime`   | private     | Fecha de creación                                 |
| updatedAt          | `DateTime`   | private     | Fecha de última actualización                     |

### Métodos

| Nombre                 | Tipo de retorno | Visibilidad | Descripción                                            |
| ---------------------- | --------------- | ----------- | ------------------------------------------------------ |
| generateRecommendation | `void`          | public      | Genera una recomendación personalizada para el usuario |
| markUpdated            | `void`          | private     | Actualiza internamente el campo `updatedAt`            |

## PlantRecommendation

| Propiedad     | Valor                                                       |
| ------------- | ----------------------------------------------------------- |
| **Nombre**    | PlantRecommendation                                         |
| **Categoría** | Value Object                                                |
| **Propósito** | Contener los parámetros de la recomendación para una planta |

### Atributos

| Nombre      | Tipo de dato | Visibilidad | Descripción                  |
| ----------- | ------------ | ----------- | ---------------------------- |
| humidity    | `String`     | public      | Recomendación de humedad     |
| light       | `String`     | public      | Recomendación de luz         |
| water       | `String`     | public      | Recomendación de riego       |
| temperature | `String`     | public      | Recomendación de temperatura |

---

#### 4.2.8.2. Interface Layer.

## RecommendationController

| Propiedad     | Valor                                                     |
| ------------- | --------------------------------------------------------- |
| **Nombre**    | RecommendationController                                  |
| **Categoría** | Controller                                                |
| **Propósito** | Exponer los servicios REST para gestionar recomendaciones |
| **Ruta**      | `/api/recommendations/`                                   |

### Métodos

| Nombre               | Ruta                            | Acción                            | Handle                        |
| -------------------- | ------------------------------- | --------------------------------- | ----------------------------- |
| getRecommendation    | `/{userId:long}/{plantId:long}` | Obtener recomendación para planta | `GetRecommendationQuery`      |
| createRecommendation | `/create`                       | Crear nueva recomendación         | `CreateRecommendationCommand` |
| updateRecommendation | `/update`                       | Actualizar recomendación          | `UpdateRecommendationCommand` |

---

#### 4.2.8.3. Application Layer.

## GetRecommendationQueryHandler

| Propiedad     | Valor                                                            |
| ------------- | ---------------------------------------------------------------- |
| **Nombre**    | GetRecommendationQueryHandler                                    |
| **Categoría** | Query Handler                                                    |
| **Propósito** | Manejar la consulta para obtener una recomendación personalizada |

## CreateRecommendationCommandHandler

| Propiedad     | Valor                                          |
| ------------- | ---------------------------------------------- |
| **Nombre**    | CreateRecommendationCommandHandler             |
| **Categoría** | Command Handler                                |
| **Propósito** | Manejar la creación de una nueva recomendación |

## UpdateRecommendationCommandHandler

| Propiedad     | Valor                                                   |
| ------------- | ------------------------------------------------------- |
| **Nombre**    | UpdateRecommendationCommandHandler                      |
| **Categoría** | Command Handler                                         |
| **Propósito** | Manejar la actualización de una recomendación existente |

---

#### 4.2.8.4. Infrastructure Layer.

## RecommendationRepository

| Propiedad     | Valor                                                                       |
| ------------- | --------------------------------------------------------------------------- |
| **Nombre**    | RecommendationRepository                                                    |
| **Categoría** | Repository Implementation                                                   |
| **Propósito** | Implementar `IRecommendationRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre       | Tipo de retorno   | Visibilidad | Descripción                            |
| ------------ | ----------------- | ----------- | -------------------------------------- |
| findByUserId | `Recommendation?` | public      | Obtener la recomendación por `userId`  |
| create       | `Unit`            | public      | Crear una nueva recomendación          |
| update       | `Unit`            | public      | Actualizar una recomendación existente |
| delete       | `Unit`            | public      | Eliminar la recomendación              |

---

#### 4.2.8.5. Bounded Context Software Architecture Component Level Diagrams.

#### 4.2.8.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.8.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-caring-intelligence/CaringIntelligenceClassDiagram.png"></image>

##### 4.2.8.6.2. Bounded Context Database Design Diagram.

<image src="../assets/img/capitulo-4/bounded-context-caring-intelligence/CaringIntelligenceDbDiagram.png"></image>

### 4.2.9. Bounded Context: Data Insights & Reporting

#### 4.2.9.1. Domain Layer.

## DataReport

| Propiedad     | Valor                                                  |
| ------------- | ------------------------------------------------------ |
| **Nombre**    | DataReport                                             |
| **Categoría** | Aggregate Root                                         |
| **Propósito** | Generar y almacenar reportes de datos para su análisis |

### Atributos

| Nombre      | Tipo de dato | Visibilidad | Descripción                                   |
| ----------- | ------------ | ----------- | --------------------------------------------- |
| reportId    | `Long`       | private     | Identificador único del reporte               |
| userId      | `Long`       | private     | Identificador del usuario asociado al reporte |
| data        | `String`     | private     | Datos relevantes del reporte                  |
| reportType  | `String`     | private     | Tipo de reporte (mensual, anual, etc.)        |
| generatedAt | `DateTime`   | private     | Fecha de generación del reporte               |
| createdAt   | `DateTime`   | private     | Fecha de creación                             |
| updatedAt   | `DateTime`   | private     | Fecha de última actualización                 |

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                 |
| -------------- | --------------- | ----------- | ------------------------------------------- |
| generateReport | `void`          | public      | Genera un nuevo reporte                     |
| markUpdated    | `void`          | private     | Actualiza internamente el campo `updatedAt` |

## DataSource

| Propiedad     | Valor                                        |
| ------------- | -------------------------------------------- |
| **Nombre**    | DataSource                                   |
| **Categoría** | Value Object                                 |
| **Propósito** | Representar la fuente de datos de un reporte |

### Atributos

| Nombre          | Tipo de dato | Visibilidad | Descripción                                     |
| --------------- | ------------ | ----------- | ----------------------------------------------- |
| sourceId        | `Long`       | private     | Identificador de la fuente de datos             |
| dataType        | `String`     | private     | Tipo de los datos (e.g., sensor, usuario, etc.) |
| dataDescription | `String`     | private     | Descripción de los datos                        |
| createdAt       | `DateTime`   | private     | Fecha de creación                               |

---

#### 4.2.9.2. Interface Layer.

## DataReportController

| Propiedad     | Valor                                                       |
| ------------- | ----------------------------------------------------------- |
| **Nombre**    | DataReportController                                        |
| **Categoría** | Controller                                                  |
| **Propósito** | Exponer los servicios REST para gestionar reportes de datos |
| **Ruta**      | `/api/data-reports/`                                        |

### Métodos

| Nombre           | Ruta                             | Acción                                      | Handle                    |
| ---------------- | -------------------------------- | ------------------------------------------- | ------------------------- |
| getReport        | `/{userId:long}/{reportId:long}` | Obtener reporte por ID de usuario y reporte | `GetDataReportQuery`      |
| createReport     | `/create`                        | Crear nuevo reporte                         | `CreateDataReportCommand` |
| updateReport     | `/update`                        | Actualizar reporte existente                | `UpdateDataReportCommand` |
| getReportsByUser | `/user/{userId:long}`            | Obtener todos los reportes de un usuario    | `GetReportsByUserQuery`   |

---

#### 4.2.9.3. Application Layer.

## GetDataReportQueryHandler

| Propiedad     | Valor                                                |
| ------------- | ---------------------------------------------------- |
| **Nombre**    | GetDataReportQueryHandler                            |
| **Categoría** | Query Handler                                        |
| **Propósito** | Manejar la consulta para obtener un reporte de datos |

## CreateDataReportCommandHandler

| Propiedad     | Valor                                            |
| ------------- | ------------------------------------------------ |
| **Nombre**    | CreateDataReportCommandHandler                   |
| **Categoría** | Command Handler                                  |
| **Propósito** | Manejar la creación de un nuevo reporte de datos |

## UpdateDataReportCommandHandler

| Propiedad     | Valor                                           |
| ------------- | ----------------------------------------------- |
| **Nombre**    | UpdateDataReportCommandHandler                  |
| **Categoría** | Command Handler                                 |
| **Propósito** | Manejar la actualización de un reporte de datos |

---

#### 4.2.9.4. Infrastructure Layer.

## DataReportRepository

| Propiedad     | Valor                                                                   |
| ------------- | ----------------------------------------------------------------------- |
| **Nombre**    | DataReportRepository                                                    |
| **Categoría** | Repository Implementation                                               |
| **Propósito** | Implementar `IDataReportRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                      |
| ------------ | --------------- | ----------- | -------------------------------- |
| findByUserId | `DataReport?`   | public      | Recupera un reporte por `userId` |
| create       | `Unit`          | public      | Crear un nuevo reporte           |
| update       | `Unit`          | public      | Actualiza un reporte existente   |
| delete       | `Unit`          | public      | Elimina un reporte               |

## DataSourceRepository

| Propiedad     | Valor                                                                   |
| ------------- | ----------------------------------------------------------------------- |
| **Nombre**    | DataSourceRepository                                                    |
| **Categoría** | Repository Implementation                                               |
| **Propósito** | Implementar `IDataSourceRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                |
| -------------- | --------------- | ----------- | ------------------------------------------ |
| findBySourceId | `DataSource?`   | public      | Recupera la fuente de datos por `sourceId` |
| create         | `Unit`          | public      | Crear una nueva fuente de datos            |
| update         | `Unit`          | public      | Actualiza una fuente de datos existente    |
| delete         | `Unit`          | public      | Elimina una fuente de datos                |

---

#### 4.2.9.5. Bounded Context Software Architecture Component Level Diagrams.

#### 4.2.9.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.9.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-data-insights-and-reporting/DataInsights&ReportingClassDiagram.png"></image>

##### 4.2.9.6.2. Bounded Context Database Design Diagram.

<image src="../assets/img/capitulo-4/bounded-context-data-insights-and-reporting/DataInsights&ReportingDbDiagram.png"></image>

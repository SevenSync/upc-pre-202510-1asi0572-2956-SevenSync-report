# Capítulo IV: Solution Software Design

En este capítulo describiremos en detalle el diseño de la solución software de Macetech, trazando desde la arquitectura general hasta los componentes y las interacciones que permiten la gestión inteligente de las macetas. Presentaremos el modelo de capas, incluyendo el servicio de adquisición y procesamiento de datos de los sensores IoT, la capa de negocio para la lógica de riego y análisis de estado de las plantas, y la capa de presentación en la aplicación móvil, así como los patrones de diseño y las tecnologías seleccionadas para garantizar escalabilidad, fiabilidad y seguridad. 

Además, se detallarán los flujos de datos, las interfaces de programación (APIs) y los protocolos de comunicación con los dispositivos, junto con las consideraciones de usabilidad y experiencia de usuario que facilitarán un manejo intuitivo y eficiente de Macetech. Por último, se abordarán aspectos claves como la integración con servicios en la nube, el manejo de eventos en tiempo real y las estrategias de despliegue continuo que soportarán la evolución continua de la plataforma.

## 4.1. Strategic-Level Domain-Driven Design

Strategic Domain-Driven Design, o DDD estratégico es un enfoque arquitectónico que busca alinear la estructura del software con la lógica del negocio y la organización. Este enfoque es esencial para gestionar la complejidad en sistemas grandes y distribuidos, especialmente cuando múltiples equipos trabajan en diferentes partes del sistema.

Según Khononov (2021), el diseño orientado al dominio enfatiza la creación de contextos delimitados ("bounded contexts") que actúan como fronteras explícitas para mantener la coherencia del modelo en cada subdominio, así como el establecimiento de un lenguaje ubicuo ("ubiquitous language") compartido entre los equipos técnicos y los expertos del negocio para asegurar una comunicación precisa y libre de ambigüedades (Khononov, 2021).

Vernon (2016) propone una clara distinción entre dos espacios complementarios: el espacio del problema, dedicado a comprender en profundidad las necesidades y restricciones del negocio, y el espacio de la solución, enfocado en diseñar y aplicar patrones técnicos y arquitectónicos que respondan eficazmente a esos requerimientos. Esta división permite alinear la estrategia empresarial con las decisiones de diseño de software (Vernon, 2016).

Para abordar las decisiones estratégicas en el diseño de software utilizando Domain-Driven Design (DDD), el equipo ha implementado un proceso estructurado que combina técnicas colaborativas y herramientas visuales. Este enfoque facilita la identificación de límites naturales dentro del dominio del negocio, conocidos como Bounded Contexts, y promueve una comprensión compartida entre todos los participantes.

### 4.1.1. EventStorming

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
*Primera fase del proceso de EventStorming de Macetech*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-1-collect-domain-events.jpg"></image>

**Fase 2: Refinamiento de Eventos de Dominio**

Con la visión global completada, el equipo realizó una segunda pasada colaborativa para:

- Eliminar duplicados y consolidar sinónimos.

- Aclarar conceptos ambiguos ajustando la redacción de cada evento.

- Ordenar cronológicamente las notas para construir una línea de tiempo coherente.

- Acordar una terminología común que garantizara consistencia semántica.

###### Figura 25
*Segunda fase del proceso de EventStorming de Macetech con la línea de tiempo y refinación de los eventos de dominio*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-2-timeline-and-refine-domain-events.jpg"></image>

###### Figura 26
*Segunda fase del proceso de EventStorming de Macetech con la recolección de eventos de dominio*

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
*Convención de color de post-its utilizados en la tercera fase del proceso de EventStorming de Macetech.*
 
 <image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-summary.jpg"></image>

 ###### Figura 28
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores.*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes.jpg"></image>

###### Figura 29
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en alertas*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-alerts.jpg"></image>

###### Figura 30
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en la obtención de datos*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-data-ingestion.jpg"></image>

###### Figura 31
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en la Administración de Identidad y Acceso*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-iam.jpg"></image>

###### Figura 32
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en las Notificaciones*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-notifications.jpg"></image>

###### Figura 33
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en la Gestión de Plantas*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-plant-management.jpg"></image>

###### Figura 34
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en la Gestión de Macetas*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-pot-management.jpg"></image>

###### Figura 35
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en las Recomendaciones*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-recommendations.jpg"></image>

###### Figura 36
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en los Reportes*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-reports.jpg"></image>

###### Figura 37
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en las Suscripciones y Membresías*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-subscriptions.jpg"></image>

###### Figura 38
*Tercera fase del proceso de EventStorming de Macetech con el rastreo de causas y disparadores en el Sistema de Riego*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-watering.jpg"></image>

Finalmente, agrupamos los eventos en torno a los agregados del dominio —elementos cohesivos de nuestro modelo— para visualizar:

- Qué comandos disparan cada evento.
- Qué roles o actores están involucrados en esos comandos.
- Qué eventos activan políticas (procesos automáticos) y qué crean modelos de lectura.

Este último paso transforma el Big Picture en un modelo estructurado, orientado a la definición de Bounded Contexts y al diseño detallado de nuestro sistema.

###### Figura 39
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them.jpg"></image>

###### Figura 40
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en las Alertas*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-alerts.jpg"></image>

###### Figura 41
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en el Ingreso de Datos*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-data-ingestion.jpg"></image>

###### Figura 42
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en la Administración de Identidad y Acceso*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-iam.jpg"></image>

###### Figura 43
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en las Notificaciones*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-notifications.jpg"></image>

###### Figura 44
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en la Gestión de Plantas*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-plant.jpg"></image>

###### Figura 45
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en la Gestión de Macetas*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-pot.jpg"></image>

###### Figura 46
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en las Recomendaciones*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-recom.jpg"></image>

###### Figura 47
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en los Reportes*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-reports.jpg"></image>

###### Figura 48
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en las Suscripciones y Membresías*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-subscriptions.jpg"></image>

###### Figura 49
*Cuarta fase del proceso de EventStorming de Macetech con la búsqueda de aggregates y su re-ordenamiento en el Sistema de Riego*

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-watering.jpg"></image>

Mediante el siguiente enlace podrá acceder y explorar en detalle la pizarra de Miro donde se desarrolló el modelo de EventStorming, organizada por fases e ilustrada con una leyenda explicativa que facilita su revisión:

<a href="https://miro.com/app/board/uXjVI7RMpGc=/?share_link_id=692821022758">Pizarra Miro del proceso de EventStorming</a>

#### 4.1.1.1 Candidate Context Discovery

En esta sección, el equipo describe detalladamente el proceso seguido para la sesión de Candidate Context Discovery, partiendo del modelo de dominio previamente construido mediante EventStorming, con el propósito de identificar y delimitar los Bounded Contexts que compondrán la arquitectura de Macetech. Según Khononov (2021), este enfoque estratégico de Domain‑Driven Design (DDD) requiere una combinación de análisis colaborativo y técnicas sistemáticas para aislar fragmentos del dominio que posean coherencia interna y aporten el mayor valor al negocio 

Para asegurar una exploración efectiva de los límites contextuales, se combinaron tres técnicas complementarias, tal como recomienda Khononov (2021):

* **Start‑with‑Value:** consiste en identificar primero aquellos subdominios o flujos de negocio cuyo impacto en la propuesta de valor sea más significativo, de modo que las decisiones de acotamiento prioricen las funcionalidades críticas para el usuario y el negocio 

* **Start‑with‑Simple:** implica descomponer el proceso principal en un conjunto mínimo de pasos secuenciales, desde el registro de usuario hasta la generación de recomendaciones, lo cual facilita la visualización y evita solapamientos entre candidatos de contexto 

* **Look‑for‑Pivotal‑Events:** se centra en detectar aquellos eventos de dominio que representan cambios de estado fundamentales, ya que estos hitos indefectiblemente marcan fronteras naturales entre contextos 

La sesión de Candidate Context Discovery, cuya duración no excedió las dos horas, se organizó como un taller interactivo en el que participaron todos los miembros de nuestro equipo de SevenSync, empleando una herramienta colaborativa de EventStorming, Miro. Durante la misma, se capturaron iterativamente pantallazos que documentan la evolución del modelo de eventos, desde la visión inicial hasta la estructuración final de los contextos. Estas imágenes se incorporarán en la sección para evidenciar la progresión metodológica y facilitar la trazabilidad de las decisiones tomadas.

A partir del modelo de dominio generado con EventStorming, el equipo explica y evidencia el proceso realizado para la sesión de Candidate Context Discovery, en la que se busca identificar los Bounded Contexts. Durante la sesión se siguieron estos pasos:

1. **Preparación y definición de alcance**

   Para garantizar una sesión estructurada y productiva, se llevaron a cabo las siguientes actividades previas: <br><br>

   - **Convocatoria y roles de los participantes**

      Se conformó un grupo interdisciplinario bajo la coordinación de SevenSync, integrado por:<br><br>
  
        - **Desarrolladores backend y frontend**, responsables de la viabilidad técnica.
    
        - **Diseñadores UX/UI**, encargados de asegurar la coherencia en la experiencia de usuario. <br><br>

    * **Definición de objetivos y alcance** <br><br>

      - **Propósito principal:** Descomponer el dominio de Macetech, desde el registro inicial del usuario hasta la emisión de recomendaciones y reportes personalizados.
  
      - **Alcance temporal:** Taller de mínimo dos horas y máximo tres horas en la plataforma Miro utilizando la técnica de EventStorming. <br><br>

    * **Herramientas y materiales de trabajo**<br><br>
  
      - **Lienzo colaborativo en Miro:** para la colocación y organización dinámica de eventos y comandos.
  
      - **Post‑its codificados por color:** diferenciando eventos de dominio, comandos de acción e integraciones externas.
  
      - **Marcadores y cámaras:** para anotar aclaraciones y capturar iteraciones de la evolución del modelo.<br><br>
  
    * **Asignación de responsabilidades** <br><br>
  
      - **Facilitador:** orientó la dinámica del taller, gestionó los tiempos y promovió la participación activa.
  
      - **Escritor:** trasladó al lienzo digital las notas y agrupaciones, asegurando la trazabilidad de cada modificación.
  
      - **Expertos de dominio:** validaron definiciones, aclararon términos y garantizaron la precisión del lenguaje ubicuo. <br><br>

2. **Técnica Start‑with‑Value**

    Con el fin de enfocar el análisis en las áreas de mayor impacto, se realizó: <br><br>

    * **Identificación de “valores núcleo”**
  
      Cada integrante propuso los flujos de negocio que, a su juicio, aportan el mayor valor a usuario y organización:<br><br>
  
        - Gestión inicial de macetas y parámetros de configuración.
  
        - Generación de recomendaciones inteligentes para maximizar la tasa de éxito en el cuidado.
  
        - Monitoreo en tiempo real, evitando pérdidas derivadas de riegos inadecuados.<br><br>
  
    * **Priorización de eventos**
  
      Se listaron todos los eventos detectados y se clasificaron según su impacto (alto, medio, bajo). Solo los catalogados como alto impacto se trasladaron a la siguiente etapa, garantizando que la sesión permaneciera centrada en las funciones críticas.<br><br>

3. **Técnica Start‑with‑Simple**

    Para clarificar la secuencia de operaciones esenciales, se procedió a:<br><br>

    *  **Modelado visual con post‑its**
 
       Cada uno de los nueve pasos se representó con post‑its de un único color, evitando superposiciones y facilitando la delimitación de responsabilidades entre los distintos subdominios.<br><br>

    * **Descomposición en pasos mínimos**
  
      Se esbozó un timeline básico que recogiera el flujo de valor, compuesto por:<br><br>

###### Tabla 13

_Flujo de valor identificado en el proceso de EventStorming de Macetech_

| Paso	 | Descripción	                                                                                                   | Artefactos de Dominio / Evento Pivotal                         |
|-------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| 1     | Registro del usuario en la plataforma.	                                                                        | Comando: RegisterUser, Evento: UserRegistered                  |
| 2	    | Creación de perfil con datos de contacto y preferencias.	                                                      | Comando: CreateProfile, Evento: ProfileCreated                 |
| 3	    | Autenticación del usuario, incluyendo verificación 2FA.	                                                       | Comando: AuthenticateUser, Evento: UserAuthenticated           |
| 4	    | Pago de suscripción a Macetech (plan seleccionado).	                                                           | Comando: ProcessSubscriptionPayment, Evento: SubscriptionPaid  |
| 5	    | Registro y configuración inicial de la maceta (Pot).	                                                          | Comando: RegisterPot, Evento: PotRegistered                    |
| 6	    | Definición de riego automático y programación de reportes periódicos.	                                         | Comando: SelectWatering, Evento: AutomaticWateringProgrammed   |
| 7	    | Identificación de la planta asociada a la maceta (catálogo de especies).	                                      | Comando: AddNewPlant, Evento: NewPlantAdded                    |
| 8	    | Captura de datos de sensores (humedad, temperatura, pH, salinidad) y obtención de contexto climático vía API.	 | SensorDataCollected + Evento: ExternalClimateDataFetched       |
| 9	    | Generación de recomendaciones y notificaciones de alertas.	                                                    | Comando: SelectRecommendation, Evento: RecommendationDisplayed |

4. **Técnica Look‑for‑Pivotal‑Events**

    Con el propósito de delimitar con precisión los contextos, se identificaron eventos de transición. Un evento de transición, según Khononov (2021), no solo marca un cambio de estado significativo, por ejemplo el paso de “usuario anónimo” a “usuario registrado” o de “maceta sin configurar” a “maceta lista para monitoreo”, sino que también permite priorizar de forma rigurosa el modelado y el desarrollo. Al centrarse en aquellos eventos de mayor impacto, el equipo puede determinar con claridad qué áreas requieren atención inmediata y cuáles funcionalidades deben implementarse primero, garantizando así que las decisiones de diseño estén siempre alineadas con los objetivos de negocio y el valor aportado al usuario.

###### Tabla 14 

*Lista de transiciones identificadas en el proceso de EventStorming de Macetech*

| Transición                   | Descripción                                                                                                                                |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| UserRegistered	              | Un usuario anónimo se convierte en un usuario registrado, creando una cuenta válida en el sistema.                                         | 
| UserProfileCreated	          | Un usuario sin perfil asocia y configura su perfil con datos de contacto y preferencias personales.                                        | 
| UserProfileDeleted	          | Un usuario con perfil configurado elimina su perfil, quedando sin datos personales asociados.                                              | 
| UserAuthenticated	           | Una sesión no iniciada se valida exitosamente según los datos ingresados por el usuario                                                    | 
| SubscriptionPaid	            | Un usuario con plan inactivo activa su suscripción mediante el pago correspondiente, habilitando acceso a funcionalidades premium.         | 
| SubscriptionCancelled	       | Un usuario con suscripción activa cancela su plan, desactivando el acceso a servicios asociados.                                           | 
| ExternalClimateDataFetched	  | El sistema integra datos climáticos externos (vía API) según la ubicación del usuario, aportando contexto ambiental a los sensores.        | 
| PotRegistered	               | Una maceta previamente no asociada se registra y vincula a un usuario, quedando disponible para su gestión.                                | 
| PotSelected	                 | El usuario selecciona una maceta de la lista de macetas registradas, estableciéndola como activa para operaciones.                         | 
| PotDeleted	                  | El usuario elimina una maceta registrada, desvinculándola completamente de su cuenta.                                                      | 
| BluetoothDevicesPaired	      | Se establece una conexión Bluetooth entre la maceta y la red del dispositivo, habilitando la comunicación inalámbrica.                     |
| IrrigationConfigured	        | Una maceta sin parámetros de riego definidos adquiere reglas y periodicidad de riego configuradas.                                         |
| PlantIdentified	             | Se reconoce la especie de la planta en la maceta y se asignan rangos óptimos de riego, temperatura, pH y salinidad.                        |
| PlantRegistered	             | Una planta identificada en maceta se vincula formalmente al usuario, completando su registro en el sistema.                                |
| PlantWatered	                | Una planta con baja humedad recibe riego, aumentando su nivel de humedad a parámetros saludables.                                          | 
| PlantDeleted	                | El usuario elimina la asociación de la planta en la maceta, quedando ésta vacía nuevamente.                                                | 
| WateringProgrammed	          | Un sistema de riego manual se transforma en un programa de riego automático para la planta especificada.                                   | 
| NotificationDisplayed	       | El sistema muestra una notificación en la bandeja del usuario sobre un evento relevante (alerta, recomendación).                           | 
| NotificationChecked	         | El usuario marca una notificación como leída, cambiando su estado a “checada” en la bandeja de notificaciones.                             | 
| NotificationDeleted	         | El usuario elimina una notificación leída, removiéndola de la bandeja de notificaciones.                                                   |
| SensorDataCaptured	          | Los sensores recaban datos brutos (humedad, temperatura, pH, salinidad) y los registran para su procesamiento.                             | 
| SensorDataDelivered	         | Los datos capturados por los sensores se envían al sistema de la aplicación, quedando disponibles para el usuario.                         | 
| SensorDataCollected	         | Un sensor pasa de no tener datos almacenados a disponer de registros de las métricas capturadas.                                           |
| SensorHistoryDisplayed	      | El sistema presenta al usuario el historial de datos de sensores, permitiendo aplicar filtros y explorar tendencias a lo largo del tiempo. |
| RecommendationGenerated	     | Con los datos recopilados, el sistema elabora recomendaciones y alertas personalizadas para el usuario.                                    |
| RecommendationDisplayed	     | El usuario visualiza en su bandeja de recomendaciones las acciones sugeridas para optimizar el cuidado de su planta.                       | 
| ConsentDelivered	            | El sistema muestra al usuario los documentos de términos y condiciones, dejando constancia de su presentación.                             |
| ConsentAccepted	             | El usuario otorga su consentimiento a los términos y condiciones, registrándose dicha aceptación en el sistema.                            |
| ConsentRejected	             | El usuario rechaza los términos y condiciones, registrándose dicha negativa en el sistema.                                                 |

  * **Agrupación por afinidad de eventos**

    Sobre el lienzo, los post‑its se reagruparon alrededor de cada evento pivotal, permitiendo visualizar con claridad los límites naturales entre posibles contextos.

5. **Visualización evolutiva**

    Con el objetivo de documentar de manera sistemática el avance del modelo y garantizar su trazabilidad, se implementó un proceso de registro visual en intervalos regulares:<BR><BR>

    * **Capturas iterativas**

    Para conservar un historial detallado de la evolución del tablero, se generaron capturas de pantalla en Miro a lo largo de toda la sesión de trabajo, siguiendo estos hitos: <br><br>

      - **Estado inicial:** todos los eventos recolectados, aún sin clasificar ni ordenar, reflejando la materia prima del modelado.
   
      - **Después de Start-with-Value:** se destacaron exclusivamente aquellos eventos con mayor repercusión en la generación de valor, lo que permitió centrar el análisis en los aspectos críticos del dominio.
   
      - **Después de Start-with-Simple:** se reorganizó el conjunto de eventos siguiendo un criterio cronológico básico, facilitando la comprensión del flujo secuencial de las interacciones.
   
      - **Después de Look-for-Pivotal-Events:** se identificaron y agruparon los eventos clave que actúan como puntos de inflexión, sentando las bases para la delimitación de subdominios.
   
      - **Versión final:** se plasmó la consolidación de los candidatos a contextos delimitados, incorporando agregados, políticas y responsabilidades, y validando la coherencia global del modelo.

  * **Registro meticuloso**
    
    Cada imagen se anotó con fecha, hora y una breve descripción de los ajustes realizados, asegurando que el informe refleje con exactitud la evolución metodológica, y facilitando la inclusión de estas evidencias en la sección correspondiente.

6. **Candidatos a Bounded Context**

A continuación presentamos la sección de Candidatos a Bounded Contexts, donde listamos todos los contextos identificados en la sesión inicial (incluyendo aquellos que finalmente no se consolidaron) y la justificación de su inclusión o exclusión en el conjunto definitivo.

###### Tabla 15

_Lista de candidatos a Bounded Context identificados en el proceso de EventStorming de Macetech_

| Contexto                         | Responsabilidades clave                                                                                                                                                                                                                                                                                                                                                                                                                                                    | ¿Pasa al diseño                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IAM                              | Autenticación (login/logout, manejo de sesiones), emisión y validación de JWT y tokens de refresco, soporte 2FA, gestión de permisos y roles. CRUD de cuentas de usuario, eliminación, recuperación de contraseña, validación de datos de contacto                                                                                                                                                                                                                         | **Consolidado:** La seguridad y control de acceso son requisitos no negociables. Al agrupar login Y emisión de tokens en un único contexto, se garantiza la consistencia en la gestión de credenciales, la separación de responsabilidades y la escalabilidad de las políticas de acceso. También es el núcleo del ciclo de vida de cuentas de usuario. Centralizar creación, actualización y baja de cuentas asegura trazabilidad de eventos y facilita la auditoría.                                                                                                                                                                                                                                               |
| Profile and Preferences          | Almacenamiento/actualización de datos de perfil, preferencias del usuario, integración Geo API, y normalización de direcciones del usuario                                                                                                                                                                                                                                                                                                                                 | **Consolidado:** Ofrece personalización y localización sin contaminar otros contextos dentro de la solución. Al abstraer el manejo de datos de perfil, contacto y preferencias, se optimiza la reutilización de la Geo API y se garantiza que las modificaciones de esquema o validaciones no afecten la lógica de negocio de autenticación ni de facturación. Esto involucra también preferencias de notificaciones, apariencia de la aplicación, etc.                                                                                                                                                                                                                                                              |
| Asset & Resource Management      | CRUD de macetas, configuración de parámetros de riego (frecuencia, volumen, límites), metadatos (nombre, ID), persistencia histórica de los datos obtenidos                                                                                                                                                                                                                                                                                                                | Este componente constituye la base de la capa IoT, ya que permite registrar las macetas junto con sus parámetros iniciales. Centralizar en este punto la configuración posibilita desacoplar la lógica de los sensores de la lógica del resto de la aplicación, lo que a su vez favorece la extensibilidad del sistema. De este modo, se pueden incorporar nuevos tipos de dispositivos sin generar impactos en los módulos de control ni en los procesos analíticos, asegurando una arquitectura más flexible y escalable.                                                                                                                                                                                          |
| Service Design and Planning      | Catálogo de especies de plantas junto con sus rangos óptimos de pH, luminosidad, temperatura y salinidad, así como la validación de la correspondencia planta–maceta. Engloba el diseño y la planificación del servicio y de sus funcionalidades, desde la selección de la especie hasta la configuración de sus parámetros.                                                                                                                                               | **Consolidado:** Este enfoque posibilita la evolución del modelo botánico de manera autónoma respecto al hardware subyacente. Al aislar la lógica del servicio de las especies y sus rangos óptimos, se facilita la incorporación de nuevas variedades vegetales o la integración de proveedores de datos externos, sin que ello afecte a otras capas. De este modo, se mantiene la robustez y la coherencia arquitectónica del sistema.                                                                                                                                                                                                                                                                             |
| Subscriptions & Payments         | Definición y gestión de los planes de suscripción, del procesamiento seguro de las transacciones y de la administración integral de las facturas, así como de la integración con pasarelas de pago y webhooks con la API externa de Stripe. De este modo, se garantiza la trazabilidad de los cobros y la coherencia en la facturación..                                                                                                                                   | **Consolidado:** Este contexto soporta tanto el modelo de negocio freemium como las suscripciones de pago. Al mantener un dominio dedicado exclusivamente a la facturación, se aísla cualquier cambio en las pasarelas de pago, en los planes tarifarios o en los flujos de cobro, evitando impactos en la lógica de usuario o en los sistemas físicos. Esta separación otorga la flexibilidad necesaria para ajustar políticas de precios y métodos de pago con el mínimo esfuerzo y sin fricciones entre módulos.                                                                                                                                                                                                  |
| Service Operation and Monitoring | Agrupa las funciones de verificación de estado (health checks), registro de logs críticos y generación y envío de alertas (push y e-mail), así como la visualización de un dashboard operativo. Además, ejecuta las operaciones de la maceta, incluyendo riego, notificaciones y recomendaciones, y supervisa el estado de la planta mediante la interacción de sensores y actuadores, integrando tanto la aplicación embebida (embedded app) como la de borde (edge app). | **Consolidado:** Este contexto centraliza la supervisión y la gestión de alertas en un único módulo, evitando la fragmentación de la lógica de notificaciones. Al consolidar la detección de fallos y su envío al usuario, se asegura la coherencia en los umbrales y en los canales de comunicación, además de facilitar la medición y optimización del uptime. Este componente constituye el núcleo del valor añadido de Macetech. Asimismo, al desacoplar el procesamiento de la ingesta de datos de las reglas de negocio, se posibilita la iteración continua en los modelos de decisión sin afectar los flujos de riego ni la analítica básica, favoreciendo la experimentación y el versionado de algoritmos. |
| Data Analytics                   | Este módulo gestiona la ingesta, normalización y almacenamiento de los registros de sensores (SensorRecord), soporta tanto el procesamiento por lotes (batch) como en tiempo real (streaming) y provee dashboards analíticos para la visualización de métricas y tendencias relevantes.                                                                                                                                                                                    | **Consolidado:** Este módulo ofrece una visibilidad completa de las operaciones y sus resultados. Al aislarlo de la capa de control, se posibilita la escalabilidad de los pipelines de datos y la configuración de políticas de retención sin afectar los servicios transaccionales, lo que facilita la incorporación de nuevas herramientas de análisis.                                                                                                                                                                                                                                                                                                                                                           |
| Caring Intelligence              | Este módulo integra un motor de recomendaciones que crea entidades Recommendation, soporta la generación de informes personalizados mediante plantillas (ReportTemplate) y emplea aprendizaje continuo para mejorar sus sugerencias de forma progresiva.                                                                                                                                                                                                                   | **Excluido:** En lugar de contar con un bounded context independiente para el motor de recomendaciones, se ha integrado completamente dentro del contexto de Service Operation and Monitoring. De este modo, las funciones de recomendación comparten la misma canalización de datos en tiempo real y los mecanismos de supervisión de dispositivos edge y embedded. Esta unificación reduce la latencia de la información y garantiza una única fuente para todas las reglas de negocio, facilitando al mismo tiempo el despliegue, la monitorización de desempeño y la iteración ágil de algoritmos sin impactar los flujos de riego ni los servicios de control.                                                  |
| Watering Management              | El motor de decisión de riego integra el análisis de los datos de los sensores (SensorData) y la configuración de la maceta (PotConfiguration) para generar automáticamente los trabajos de riego (IrrigationJob), gestionar posibles excepciones y coordinar su ejecución con la capa IoT.                                                                                                                                                                                | **Excluido:** En lugar de mantener un bounded context independiente para el riego, esta responsabilidad se ha trasladado al nuevo contexto Service Operation and Monitoring. De este modo, las funciones de control físico, supervisión y excepción se agrupan junto con el resto de operaciones IoT, mejorando la cohesión y la claridad de la arquitectura. Asimismo, se ha prescindido de la planificación de riego tradicional, dado que el sistema opera exclusivamente en función de lecturas en tiempo real de los sensores, lo que simplifica el flujo de datos y evita duplicidades en la lógica de control.                                                                                                |
| Notifying System                 | Este módulo se encarga del envío y la gestión de notificaciones genéricas, sin incluir información adicional ni vinculación con recomendaciones o alertas específicas.                                                                                                                                                                                                                                                                                                     | **Excluido:** Su ámbito limitado, centrado exclusivamente en el envío de notificaciones genéricas, carecía de un modelo de datos sólido y presentaba solapamientos con las alertas críticas. Por ello, se ha integrado dentro del contexto de Service Operation and Monitoring, centralizando la supervisión y los canales de comunicación para eliminar la duplicación de lógica y reforzar la consistencia operativa.                                                                                                                                                                                                                                                                                              |
| Critical Alert System            | Se encarga de detectar y disparar alertas críticas basadas en umbrales específicos para las métricas de las plantas, garantizando una respuesta inmediata ante cualquier desviación que pueda comprometer su salud.                                                                                                                                                                                                                                                        | **Excluido:** Este componente duplicaba responsabilidades con el contexto de supervisión general y carecía de un modelo de datos y reglas propio. Por ello, su lógica se consolidó en «Service Operation and Monitoring», que centraliza y armoniza todas las alertas, eliminando redundancias y asegurando una única fuente de verdad.                                                                                                                                                                                                                                                                                                                                                                              |
| AI Service                       | Servicio de inteligencia artificial orientado al procesamiento de datos, pero sin un enfoque claro en generar recomendaciones personalizadas para cada planta ni en la definición precisa de alertas, lo que limitaba su aplicabilidad directa dentro del flujo operativo.                                                                                                                                                                                                 | **Excluido:** Este módulo resultaba excesivamente genérico y desalineado tanto de los casos de uso concretos como de los objetivos del proyecto. Se reemplazó por integraciones más focalizadas: la gestión de plantas recae ahora sobre la Plant API dentro del contexto de Service Design and Planning, mientras que la lógica de recomendaciones y el aprendizaje automático se integra por completo en Service Operation and Monitoring, asegurando un procesamiento de datos contextualizado, coherente y alineado con las necesidades operativas.                                                                                                                                                              |
| SensorState                      | Se encarga de la gestión remota del ciclo de vida y estado físico de los sensores, incluyendo calibración, detección de fallos y mantenimiento preventivo, para garantizar su operatividad continua y fiabilidad.                                                                                                                                                                                                                                                          | **Excluido:** La gestión remota de calibraciones, fallos y ciclos de vida de los sensores implicaba un dominio especializado en ingeniería de hardware que excedía el alcance principal del proyecto. Por ello, se optó por excluir este bounded context y conservar el foco en el desarrollo del software y la operatividad del sistema IoT.                                                                                                                                                                                                                                                                                                                                                                        |

**7. Bounded Contexts finales**

Como resultado de la sesión de Candidate Context Discovery y tras identificar los eventos cruciales (pivotal events), se definieron y refinaron siete Bounded Contexts a partir de los candidatos iniciales. Para cada uno se establecieron sus responsabilidades principales, su lenguaje ubicuo y los contratos de integración, garantizando así una delimitación clara y coherente entre dominios.

###### Tabla 16

_Lista de Bounded Context finales identificados en el proceso de EventStorming de Macetech_

| Contexto                                | Responsabilidades clave                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Ubiquitous Language                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **1. IAM**                              | **- Autenticación de usuarios:** gestión de inicio y cierre de sesión, con control seguro de las credenciales. <br>**- Emisión y validación de tokens:** generación de JSON Web Tokens (JWT) y tokens de refresco para mantener sesiones seguras y persistentes. <br> **- Autenticación de dos factores (2FA):** envío y verificación de códigos para reforzar la seguridad de acceso. <br> **- Gestión de permisos y roles:** definición, asignación y verificación de privilegios de usuario según políticas establecidas. <br> **- Registro y administración de cuentas:** creación de usuarios, recuperación de contraseñas y mantenimiento de perfiles.                                                                                                                                                                                                                                                                                                                                                                                                                              | **- User:** Representa a la persona real o entidad que interactúa con el sistema, identificada de forma única por un conjunto de atributos. <br> **- Credentials** Conjunto de datos secretos que el usuario emplea para demostrar su identidad.<br> **- Session:** Período de interacción autorizado entre un usuario y el sistema, iniciado tras la autenticación y mantenido mediante un token válido hasta que el usuario cierre sesión o expire. <br> **- Access Token:** Token de corta duración que certifica las credenciales del usuario y autoriza el acceso a recursos protegidos durante la sesión activa. <br> **- Refresh Token:** Token de mayor duración que permite obtener nuevos Access Tokens sin necesidad de que el usuario vuelva a autenticarse con sus credenciales. <br> **-Two‑Factor Authentication (2FA):** Mecanismo de seguridad adicional que exige un segundo factor de verificación (p. ej., código enviado por SMS o app de autenticación) tras la introducción de las credenciales.                                                                                        |
| **2. Profile & Personal Data**          | - **Gestión de perfil de usuario:** almacenamiento y actualización de datos personales (nombre, teléfono, dirección) con controles de integridad. <br> - **Configuración de preferencias:** personalización de idioma y modelo de notificaciones a recibir. <br> **- Integración con Geo API:** acceso a catálogos de países y ciudades para facilitar la selección y estandarización de ubicaciones. <br> - **Normalización y validación de direcciones:** aplicación de reglas y formatos estándar para asegurar la consistencia de los datos de ubicación.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | - **User:** Representa al individuo registrado en el sistema, con una identidad única vinculada a su perfil y credenciales de acceso. <br> - **Profile:** Conjunto de datos personales y configuraciones asociadas a un usuario, incluyendo nombre, dirección, número de teléfono y preferencias. <br> - **Address:** Información estructurada sobre la ubicación física del usuario (país, ciudad, calle, código postal), sujeta a validación y normalización. <br> - **PhoneNumber:** Número de contacto del usuario, almacenado en formato internacional estandarizado y utilizado para verificación o notificaciones. <br> - **Preference:** Opciones personalizables elegidas por el usuario, como idioma, configuración de notificaciones, y tema de interfaz (modo claro/oscuro). <br> -**PasswordRecoveryToken:** Token temporal generado para permitir la recuperación segura de una cuenta en caso de pérdida de contraseña. - **GeoAPI:** Servicio externo que proporciona catálogos actualizados de países y ciudades para facilitar la selección geográfica y la validación de direcciones.       |
| **3. Asset & Resource Management**      | - **Gestión de macetas (Pot):** operaciones de creación, lectura, actualización y eliminación de instancias de Pot, garantizando la integridad y consistencia de los datos. <br> - **Configuración de riego:** definición de parámetros clave, como frecuencia, volumen y umbrales de activación, para adaptar el riego a las necesidades de cada planta. <br>- **Administración de metadatos:** asignación de atributos descriptivos (nombre, identificador único y etiquetas) que facilitan la organización, búsqueda y categorización de las macetas. <br> -**Registro histórico de configuraciones:** persistencia de todos los ajustes realizados en cada maceta, permitiendo auditorías y análisis de evolución a lo largo del tiempo.                                                                                                                                                                                                                                                                                                                                              | - **Pot:** Representa la maceta física asociada a una planta, identificada por un ID único y un conjunto de atributos básicos.<br> -**PotConfiguration:** Conjunto de parámetros de riego y operación asignados a una maceta determinada (frecuencia, volumen, umbrales), que define cómo debe actuarse sobre ella. <br> -**Threshold:** Valor límite que, al ser superado por una medida (humedad, temperatura, etc.), desencadena una acción automática de riego o alerta. <br> -**Metadata:** Atributos descriptivos de la maceta, como nombre, etiquetas, fecha de creación, destinados a facilitar la búsqueda y categorización. <br> - **HistoricalConfig:** Registro inmutable de las configuraciones previas de la maceta, utilizado para auditoría y análisis de evolución en el tiempo. <br> -**SensorBinding:** Asociación de la maceta con uno o varios sensores específicos, que permite la ingestión de datos ambientales para toma de decisiones. <br> -**IrrigationJob:** Tarea disparada en tiempo real que ejecuta el acto de riego sobre la maceta, según su PotConfiguration y Thresholds. |
| **4. Service Design and Planning**      | -**Catálogo de especies vegetales (PlantSpecies):** Incluye los atributos técnicos de cada planta y sus rangos óptimos de pH, luminosidad, humedad, temperatura y salinidad, garantizando una base de datos exhaustiva para el cuidado botánico. <br> -**Validación de compatibilidad planta–maceta:** Comprueba que las características de la planta seleccionada se ajusten a las dimensiones y capacidades de la maceta, evitando errores de configuración y optimizando el desarrollo vegetal. <br> -**Sincronización con APIs externas:** Ejecuta actualizaciones periódicas para incorporar nuevas especies y refrescar parámetros existentes, asegurando que el catálogo se mantenga alineado con la información más reciente del sector. <br> -**Diseño y planificación del servicio:** Abarca desde la selección de la especie hasta la definición de sus parámetros personalizados,  incluyendo frecuencia y volumen de riego, y la programación de los horarios de riego, proporcionando un flujo de trabajo completo y coherente para la gestión automatizada de cada planta. | - **PlantSpecies:** Entidad que representa una especie vegetal, con atributos como nombre científico, nombre común y clasificación botánica. <br> - **OptimalRange:** Conjunto de valores óptimos para indicadores clave (pH, luminosidad, temperatura, salinidad, humedad) que definen el entorno ideal de crecimiento de una especie. <br> - **Compatibility:** Relación que valida la adecuación entre una especie y una maceta o ambiente determinado, asegurando que las condiciones físicas y de espacio sean apropiadas. <br> - **PlantAPI:** Servicio interno responsable de proporcionar catálogos de especies y actualizar parámetros botánicos de forma periódica. <br> - **PlantParameter:** Conjunto de parámetros personalizados vinculados a una instancia de PlantSpecies (por ejemplo, ajustes finos de frecuencia y volumen de riego).                                                                                                                                                                                                                                                       |
| **5. Service Operation and Monitoring** | -**Motor de decisión de riego:** analiza en tiempo real los datos de los sensores (SensorData) junto con la configuración de la maceta (PotConfiguration), generando automáticamente los trabajos de riego (IrrigationJob) y disparando las válvulas correspondientes. <br> - **Supervisión continua:** a través de health checks, registro y almacenamiento de logs críticos, envía datos de métricas de disponibilidad y rendimiento. <br> -**Sistema de alertas:** envía notificaciones (push, correo electrónico) ante umbrales o errores, garantizando respuestas inmediatas a incidentes. <br> -**Monitoreo de dispositivo embebido y edge:** integra la aplicación embebida y edge para garantizar la trazabilidad de cada componente y operación de la maceta (riego, alertas, recomendaciones). <br> -**Motor de recomendaciones:** sistema basado en reglas sobre los sensores de Pot y los datos obtenidos con PlantAPI, que crea entidades Recommendation mapeadas a patrones de uso y genera reportes personalizados (ReportTemplate).                                       | - **IrrigationJob:** Tarea disparada en tiempo real que ejecuta el riego de una maceta, a partir de la configuración y los datos sensoriales. <br> - **ValveCommand:** Instrucción enviada al actuador de riego (válvula) para abrir o cerrar el flujo de agua según el plan de riego. <br> -**SensorData:** Lectura cruda proveniente de los sensores (humedad, temperatura, luminosidad, pH, etc.) asociada a una maceta en un instante de tiempo. <br> -**Alert:** Evento generado cuando una métrica o condición supera un umbral crítico, disparando un flujo de notificación y posibles acciones de mitigación. <br> -**NotificationChannel:** Medio utilizado para enviar alertas o avisos al usuario o al equipo de operaciones (push, correo electrónico). <br> -**Recommendation:** Sugerencia generada por el sistema de recomendaciones que propone acciones de cuidado o ajustes personalizados para la planta. <br> -**ReportTemplate:** Estructura predefinida que define el formato y contenido de los informes personalizados que se entregan al usuario.                                     |
| **6. Subscriptions & Payments**         | **-Definición y gestión de planes de suscripción (SubscriptionPlan):** creación y parametrización de modalidades (freemium, premium mensual o anual), con reglas de acceso y beneficios asociados. <br> - **Procesamiento de pagos:** manejo de transacciones periódicas y cargos únicos, garantizando la fiabilidad y la seguridad en cada operación. <br> - **Administración de facturación (Invoice):** generación automática de facturas, seguimiento de su estado (pendiente, pagada, vencida) y emisión de recordatorios ante impagos. <br> -**Integración con pasarelas de pago y webhooks:** conexión con el proveedor externo de Stripe para la ejecución de pagos y recepción de notificaciones en tiempo real sobre eventos de cobro.                                                                                                                                                                                                                                                                                                                                          | -**SubscriptionPlan:** Modelo que describe las modalidades de suscripción (freemium, premium mensual o anual), con sus características, precios y reglas de renovación. <br> -**Invoice:** Documento que detalla los cargos generados para un usuario, incluyendo desgloses de precio y fechas de vencimiento, así como su estado de pago. <br> -**PaymentTransaction:** Registro de cada intento de cobro o pago (recurrente o único), con información sobre el resultado y cualquier código de error. <br> -**Stripe API (PaymentGateway):** Servicio externo encargado de procesar los pagos, al que se envían las transacciones para su autorización y liquidación. <br> -**WebhookEvent:** Mensaje entrante desde la pasarela de pago que notifica al sistema sobre cambios en el estado de una transacción (aprobada, rechazada, reembolsada). <br> -**BillingCycle:** Periodo de facturación asociado a un SubscriptionPlan, que determina la cadencia de generación de Invoice y la programación de PaymentTransaction.                                                                                |
| **7. Data Analytics**                   | -**Ingesta, normalización y almacenamiento de registros de sensores (SensorRecord):** captura masiva de datos crudos, aplicación de procesos de limpieza y estructuración, y persistencia segura en el repositorio de datos. <br> -**Procesamiento batch y en streaming:** cálculo de métricas agregadas en lotes programados y en tiempo real, garantizando la disponibilidad continua de indicadores. <br> -**Exposición de dashboards y endpoints de consulta:** provisión de interfaces gráficas y APIs REST para la visualización interactiva de tendencias y la obtención directa de datos. - **Interpretación de KPIs:** elaboración de indicadores clave de rendimiento derivados de los datos sensoriales, facilitando la toma de decisiones operativas y estratégicas.                                                                                                                                                                                                                                                                                                          | -**SensorRecord:** Registro individual de datos capturados por un sensor (humedad, temperatura, luminosidad, pH, etc.), almacenado con su marca de tiempo y metadatos de origen. <br> -**InsightReport:** Documento generado a partir del análisis de los datos sensoriales y KPIs, que presenta conclusiones, tendencias y recomendaciones operativas o estratégicas. <br> -**Dashboard:** Interfaz gráfica interactiva que muestra visualizaciones en tiempo real o históricas de métricas clave, permitiendo filtrar y profundizar en la información. <br> -**BatchProcess:** Flujo de trabajo periódico que procesa grandes volúmenes de SensorRecord para calcular métricas agregadas y generar nuevos InsightReport. <br> -**KPI (Key Performance Indicator):** Métrica derivada de los datos sensoriales que cuantifica el rendimiento o estado de las macetas y plantas, usada para la toma de decisiones.                                                                                                                                                                                             |

#### 4.1.1.2 Domain Message Flows Modeling

En esta sección, el equipo presenta y documenta de forma detallada el proceso seguido para ilustrar la colaboración entre los distintos bounded contexts al abordar los casos de uso planteados por los usuarios del sistema. A través de la aplicación de la técnica de visualización Domain Storytelling, se evidenciará cada interacción y flujo de información entre los contextos, apoyándose en capturas de pantalla que muestran los diagramas elaborados durante el ejercicio. Este enfoque colaborativo permite validar y ajustar las fronteras de los dominios, garantizando que el diseño del software refleje fielmente las necesidades del negocio y del usuario.

Domain Storytelling es una técnica visual y ágil que utiliza historias narradas y representadas gráficamente para describir cómo los distintos actores y componentes del sistema interactúan en situaciones reales. Cada flujo se descompone en pasos secuenciales que combinan narración textual y símbolos estandarizados (actores, mensajes y artefactos), facilitando la comprensión colectiva y la detección temprana de inconsistencias o vacíos en el modelo de dominio (Hofer & Schwentner, 2021).

###### Figura 50
*Domain Message Flow relacionado a la creación de una cuenta*

<image src="../assets/img/capitulo-4/domain-message-flows-modelling/0.png" width="650px" alt="Account Creation Domain Message Flow"></image>

###### Figura 51
*Domain Message Flow relacionado a la creación de un perfil tras el primer inicio de sesión del usuario*

<image src="../assets/img/capitulo-4/domain-message-flows-modelling/1.png" width="650px" alt="Create Profile On First Sign In Domain Message Flow"></image>

###### Figura 52
*Domain Message Flow relacionado a la asignación de una maceta con un usuario específico*

<image src="../assets/img/capitulo-4/domain-message-flows-modelling/2.png" width="650px" alt="Pot Linking With User Domain Message Flow"></image>

###### Figura 53
*Domain Message Flow relacionado a la asignación de una planta a una maceta específica*

<image src="../assets/img/capitulo-4/domain-message-flows-modelling/3.png" width="650px" alt="Assign Plant to Linked Pot Domain Message Flow"></image>

###### Figura 54
*Domain Message Flow relacionado al envío de alertas provenientes de una maceta*

<image src="../assets/img/capitulo-4/domain-message-flows-modelling/4.png" width="650px" alt="Send Alert Based On Pot
 Domain Message Flow"></image>

###### Figura 55
*Domain Message Flow relacionado al proceso de decisión, ejecución y notificación de irrigación para una maceta*

<image src="../assets/img/capitulo-4/domain-message-flows-modelling/6.jpg" width="650px" alt="Decision, Execution and Notification of Irrigation
 Domain Message Flow"></image>

###### Figura 56
*Domain Message Flow relacionado a la petición del sistema automático para el plan de irrigación de una maceta*

<image src="../assets/img/capitulo-4/domain-message-flows-modelling/5.jpg" width="650px" alt="Automatic System Requests the Irrigation Plan
 Domain Message Flow"></image>

#### 4.1.1.3 Bounded Context Canvases

En esta sección, el equipo define y documenta sus candidate bounded contexts, aplicando criterios de diseño que priorizan su relevancia para los objetivos del proyecto. Mediante un enfoque iterativo, se selecciona cada bounded context por orden de importancia y se elabora su correspondiente Bounded Context Canvas. Cada canvas incluirá la descripción general del contexto, su lenguaje ubicuo, reglas de negocio, capacidades clave y dependencias, lo que permitirá visualizar de forma estructurada cómo encaja cada dominio dentro de la arquitectura global.

El Bounded Context Canvas es una herramienta que guía el diseño de dominios acotados mediante una serie de pasos sistemáticos: Context Overview Definition (visión general del contexto), Business Rules Distillation & Ubiquitous Language Capture (extracción de reglas de negocio y captura del lenguaje ubicuo), Capability Analysis (análisis de capacidades), Capability Layering (si aplica, para organizar las capacidades en capas), Dependencies Capture (identificación de dependencias con otros contextos) y Design Critique (revisión y refinamiento del diseño). Este proceso iterativo facilita la coherencia del modelo y la alineación con las necesidades del negocio, garantizando una arquitectura robusta y adaptable (Richards & Ford, 2025).

1. **Asset & Resource Management:** Registro y configuración de macetas y sus parámetros iniciales. Primer contacto del usuario con Macetech; sin él no puede comenzar ningún flujo de riego ni supervisión.

2. **Service Operation and Monitoring:** Ejecución de riegos, supervisión de salud del sistema, alertas y recomendaciones. Core, valor añadido, convierte datos en acción inmediata y feedback al usuario.

3. **Service Design and Planning:** Catálogo de especies con PlantAPI y validación planta–maceta. Base del modelo botánico que alimenta el motor de operación y las recomendaciones.

4. **Data Analytics:** Ingesta, procesamiento batch/stream y dashboards de KPIs. Muy útil para la evolución del producto, pero de valor más estratégico y menos crítico en el día a día del usuario.

5. **Profile & Personal Data:** Gestión de datos de usuario, preferencias y localización.. Personaliza la experiencia y es prerequisito para las notificaciones y segmentación.

6. **Subscriptions & Payments:** Planes de suscripción, procesamiento de pagos y facturación. Habilita el modelo freemium/pago; asegura la viabilidad económica del servicio.

7. **IAM (Authentication & Authorization):** Login/logout, gestión de sesiones, emisión de JWT. Fundamental para la seguridad y el acceso, pero en la práctica “soporta” a todos los demás contextos.

###### Figura 57
*Bounded Context Canvas de IAM (Identity and Access Management)*

<image src="../assets/img/capitulo-4/bounded-context-canvases/iam.png" width="650px" alt="Iam Bounded Context Canvas"></image>

###### Figura 58
*Bounded Context Canvas de Profile and Preferences*

<image src="../assets/img/capitulo-4/bounded-context-canvases/profile-and-personal-data.png" width="650px" alt="Profile and Preferences Bounded Context Canvas"></image>

###### Figura 59
*Bounded Context Canvas de Asset & Resource Management*

<image src="../assets/img/capitulo-4/bounded-context-canvases/pot-management.png" width="650px" alt="Asset & Resource Management Bounded Context Canvas"></image>

###### Figura 60
*Bounded Context Canvas de Subscriptions and Payments*

<image src="../assets/img/capitulo-4/bounded-context-canvases/subscriptions-and-payments-canvas.png" width="650px" alt="Suscriptions and Payments Management Bounded Context Canvas"></image>

###### Figura 61
*Bounded Context Canvas de Service Design and Planning*

<image src="../assets/img/capitulo-4/bounded-context-canvases/service-design-and-planning-canvas.png" width="650px" alt="Service Design and Planning Bounded Context Canvas"></image>

###### Figura 62
*Bounded Context Canvas de Service Operation and Monitoring*

<image src="../assets/img/capitulo-4/bounded-context-canvases/service-operation-and-monitoring-canvas.png" width="650px" alt="Service Operation and Monitoring Bounded Context Canvas"></image>

###### Figura 63
*Bounded Context Canvas de Data Analytics*

<image src="../assets/img/capitulo-4/bounded-context-canvases/data-analytics-canvas.png" width="650px" alt="Data Analytics Bounded Context Canvas"></image>

### 4.1.2. Context Mapping

En esta sección, el equipo documenta el proceso de elaboración de varios context maps, diagramas que muestran las relaciones estructurales y de dependencia entre los bounded contexts definidos previamente. A partir de la información recolectada en las sesiones de Candidate Context Discovery y los Bounded Context Canvases, se generan diseños candidatos que permiten visualizar claramente los flujos de datos, las integraciones y los puntos de acoplamiento. El objetivo es iterar sobre estas propuestas hasta dar con la topología más coherente y sostenible para la arquitectura de Macetech.

El context mapping, en el marco de Domain‑Driven Design, consiste en representar gráficamente las interacciones y contratos entre contextos, identificando patrones de relación como Shared Kernel, Customer/Supplier, Conformist o Anti‑corruption Layer. Estas visualizaciones no solo facilitan la detección de acoplamientos indeseados, sino que también aportan una visión holística de cómo los distintos módulos colaboran y comparten responsabilidades dentro del dominio. Al emplear context maps, el equipo puede evaluar de manera objetiva los trade‑offs de cada diseño y alinear la estructura de software con la estrategia de negocio.

Para guiar el proceso de refinamiento, se plantean preguntas estratégicas en cada iteración: “¿qué pasaría si movemos esta capability a otro bounded context?”, “¿qué tal si descomponemos un sub‑capability y lo trasladamos?”, “¿qué implicaría partir un contexto en dos?”, o “¿qué ganamos duplicando cierta funcionalidad para eliminar dependencias?”. Asimismo, se evalúa la conveniencia de introducir servicios compartidos o aislar los core capabilities en contextos específicos. Cada alternativa se debate contrastando su impacto en la cohesión, el acoplamiento y la escalabilidad, hasta consensuar el mapping óptimo para el ecosistema de Macetech (Khononov, 2021).

###### Figura 64 - 70
*Context Mapping de ...*

### 4.1.3. Software Architecture

La visión general de la arquitectura describe la estructura fundamental de un sistema, abarcando sus componentes principales y la interacción entre ellos. En el contexto de desarrollo de aplicaciones móviles, una arquitectura sólida es esencial para garantizar que la aplicación sea escalable, segura y eficiente. Este enfoque permite una implementación ordenada, donde cada parte del sistema tiene una responsabilidad clara, y facilita la integración de nuevas funcionalidades o la modificación de las existentes sin afectar la estabilidad general de la plataforma (Richards & Ford, 2021).

El diseño arquitectónico de Macetech se basa en una arquitectura modular, donde cada componente del sistema está desacoplado, permitiendo un desarrollo y mantenimiento más flexible. Este enfoque se apoya en patrones de diseño como el Modelo-Vista-Controlador (MVC) y el modelo de Vista-Modelo-Vista (MVVM), que promueven una clara separación de preocupaciones y mejoran la mantenibilidad del código. Además, se integra con servicios externos de autenticación, bases de datos en la nube, y plataformas de análisis, asegurando que la aplicación pueda manejar grandes volúmenes de datos de manera eficiente y con una alta disponibilidad.

La arquitectura también contempla la seguridad como un aspecto central, con la implementación de técnicas de cifrado para proteger los datos sensibles del usuario y garantizar que las comunicaciones dentro de la aplicación sean seguras. Además, se diseña para ser compatible con diversas plataformas móviles, adaptándose a las especificaciones de iOS y Android, lo que facilita una experiencia de usuario consistente y de alta calidad en ambos entornos.

De acuerdo con Brown (2023), el modelo C4 para la diagramación y esquematización de la arquitectura de software ofrece un enfoque estructurado y escalable que facilita la descripción clara de sus secciones y componentes. Al dividir la arquitectura en cuatro niveles, Contexto, Contenedores, Componentes y Código, permite una comprensión más accesible tanto para técnicos como para partes interesadas sin experiencia técnica. Esta estructura promueve una comunicación más fluida y efectiva entre los equipos de desarrollo y las partes involucradas, optimizando el proceso colaborativo y resultando en un desarrollo más eficiente y en una arquitectura de software más robusta y mantenible.

#### 4.1.3.1. Software Architecture System Landscape Diagram

El diagrama de landscape o paisaje del sistema corresponde al nivel organizacional del modelo C4 y ofrece una visión integral de todos los sistemas de software relevantes y sus interacciones dentro de un entorno empresarial o tecnológico más amplio. Este tipo de visualización resulta clave para comprender arquitecturas distribuidas, ya que permite mapear tanto sistemas internos como externos, así como los flujos de información que los conectan (Brown, 2023).

En el caso de Macetech, una plataforma de jardinería inteligente, el diagrama de landscape ilustra la convivencia e integración de múltiples componentes: desde las aplicaciones cliente (web y móvil), el backend monolítico y los servicios embebidos y edge en dispositivos IoT, hasta sistemas externos. Esta representación facilita la comprensión de relaciones críticas entre componentes distribuidos, revelando dependencias tecnológicas y posibles puntos de desacoplamiento.

Al proporcionar una vista de alto nivel, este diagrama apoya la toma de decisiones arquitectónicas estratégicas y orienta la evolución del sistema hacia estructuras más modulares, resilientes y escalables.

###### Figura 71
*Diagrama de paisaje de la plataforma de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-MacetechLandscape.png"></image>

#### 4.1.3.2. Software Architecture Context Level Diagrams

El diagrama de contexto, como nivel más alto de abstracción del modelo C4, ofrece una visión global del sistema de Macetech y su entorno externo, mostrando las interacciones de alto nivel con actores y servicios externos. Esta representación clarifica cómo la plataforma se vincula con usuarios (jardineros novatos y experimentados), sistemas externos (Stripe, GeoAPI) y otros subsistemas independientes que se pueda requerir, estableciendo los límites de responsabilidad de Macetech (Brown, 2023).

Para SevenSync, el diagrama de contexto expone de forma precisa las conexiones críticas entre Macetech y sus dependencias externas, como APIs de pasarelas de pago y proveedores de geolocalización. Al visualizar estos enlaces, el equipo puede asegurar una experiencia de usuario fluida y resiliente, anticipar puntos de fallo y planificar estrategias de desacoplamiento o sustitución de servicios, adaptándose ágilmente a las exigencias del mercado de jardinería inteligente.

###### Figura 72
*Diagrama de contexto de la plataforma de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-SystemContext.png"></image>

#### 4.1.3.2. Software Architecture Container Level Diagrams.

El diagrama de contenedores, ubicado en un nivel intermedio del modelo C4, ofrece una visión detallada de la arquitectura interna de Macetech, identificando los principales contenedores (aplicaciones cliente, servicios backend, bases de datos, aplicaciones relacionadas a IoT) y sus protocolos de comunicación. Esta representación facilita la comprensión de cómo cada pieza colabora para cumplir con los casos de uso del sistema, permitiendo al equipo técnico y a los stakeholders visualizar claramente responsabilidades, flujos de datos y tecnologías empleadas (Brown, 2023).

En el contexto de Macetech, el diagrama presenta, por ejemplo, la aplicación web y móvil como contenedores de presentación que interactúan con un backend monolítico para autenticación y lógica de negocio. A su vez, se distinguen las aplicaciones edge y embedded, las cuales conforman contenedores que se comunican con el backend a través de MQTT, cerrando así el ciclo de información en tiempo real. Esta estructura modular apoya la escalabilidad del producto y facilita la identificación de puntos de desacoplamiento o de refactorización futura.

###### Figura 73
*Diagrama de contenedores de la plataforma de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-Containers.png"></image>

###### Figura 74
*Diagrama de componentes de la Landing Page de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-LandingPageComponents.png"></image>

###### Figura 75
*Diagrama de componentes del SPA (Single-Page Application) de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-WCAComponents.png"></image>

###### Figura 76
*Diagrama de componentes del Mobile Application de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-MobileAppComponents.png"></image>

###### Figura 77
*Diagrama de componentes del Cloud API de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-MonolithComponents.png"></image>

###### Figura 78
*Diagrama de componentes del Edge Application de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-EdgeComponents.png"></image>

###### Figura 79
*Diagrama de componentes del Embedded Application de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-EmbeddedComponents.png"></image>

#### 4.1.3.3. Software Architecture Deployment Diagrams

El diagrama de despliegue muestra la distribución física de los contenedores de software sobre la infraestructura tecnológica, detallando nodos (servidores, dispositivos IoT, gateways) y las conexiones de red que los interconectan. Este nivel del modelo C4 permite visualizar dónde se ejecuta cada componente, desde el backend y las bases de datos hasta la aplicación embebida y edge, así como los protocolos de comunicación, volúmenes de tráfico y requisitos de seguridad y redundancia (Brown, 2023).

En el caso de Macetech, el diagrama de despliegue ilustra cómo se alojan las aplicaciones cliente (web y móvil), cómo interactúan con el backend monolítico y cómo se conectan los dispositivos embedded y edge mediante MQTT sobre redes. Además, se especifican los nodos de bases de datos y las pasarelas de API externas (de pago, geolocalización). Esta visión facilita la planificación de escalabilidad, alta disponibilidad y recuperación ante desastres, asegurando un despliegue robusto y mantenible.

###### Figura 80

*Diagrama de despliegue de la plataforma de Macetech*

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-Deployment-001.png"></image>

## 4.2. Tactical-Level Domain-Driven Design

En esta sección, el equipo aborda el diseño táctico de la solución siguiendo los principios de Domain‑Driven Design (DDD), traduciendo los Bounded Contexts previamente definidos en patrones y estructuras de código concretos. Cada subcapítulo se centra en uno de los contextos, describiendo sus agregados, repositorios, servicios de dominio y fábricas, así como las variantes y contratos que rigen su comportamiento interno. De este modo, se conecta la visión estratégica del dominio con decisiones de implementación precisas, garantizando que el software refleje fielmente las reglas de negocio y mantenga la coherencia del lenguaje ubicuo.

Para cada Bounded Context, se propone una arquitectura modular basada en capas tácticas, modelos de entidad, lógica de dominio, interfaces de infraestructura y adaptadores, y se aplican patrones de diseño. Además, se incluyen diagramas de clases. Este enfoque permite iterar rápidamente sobre el diseño interno sin perder alineación con los objetivos del negocio ni generar acoplamientos indebidos entre contextos (Ford et al., 2021).

### 4.2.1. Bounded Context: IAM (Identity and Access Management)

En el contexto táctico, el Bounded Context IAM (Identity and Access Management) agrupa toda la funcionalidad relacionada con la identificación, autenticación y autorización de los usuarios de Macetech. Este módulo centraliza el ciclo de vida de las cuentas: desde el registro y recuperación de credenciales hasta la gestión segura de sesiones. Incluye la generación y validación de JSON Web Tokens (access y refresh tokens) para mantener la persistencia de las sesiones sin comprometer la seguridad. Además, IAM ejerce el control de permisos y roles, definiendo y verificando privilegios de usuario conforme a las políticas establecidas, y expone interfaces limpias para su consumo por otros bounded contexts, garantizando una fuente única de verdad en toda la plataforma.

#### 4.2.1.1. IAM Bounded Context Domain Layer

En la capa de dominio de IAM se definen las entidades y objetos de valor esenciales junto con sus reglas de negocio. Además, en este nivel residen los Domain Services encargados de orquestar procesos complejos, garantizando la coherencia y la reutilización de toda la lógica central.

**User**

###### Tabla 17

_Tabla de User en el Domain Layer de IAM_

| Propiedad     | Valor                                                                                                            |
|---------------|------------------------------------------------------------------------------------------------------------------|
| **Nombre**    | User                                                                                                             |
| **Categoría** | Aggregate Root                                                                                                   |
| **Propósito** | Representar a un usuario autenticado en el sistema, encapsulando su información personal, credenciales y estado. |

###### Tabla 18

_Tabla de atributos de User en el Domain Layer de IAM_

| Nombre      | Tipo de dato    | Visibilidad | Descripción                                               |
|-------------|-----------------|-------------|-----------------------------------------------------------|
| Id          | `unsigned long` | private     | Identificador único del usuario                           |
| FullName    | `FullName`      | private     | 	Nombre completo del usuario                              |
| Email       | `Email`         | private     | 	Correo electrónico asociado al usuario                   |
| Password    | `PasswordHash`  | private     | Hash seguro de la contraseña                              |
| Role        | `List<Role>`    | private     | Lista de roles asignados al usuario                       |
| CreatedDate | `DateTime`      | private     | 	Fecha de creación del registro del usuario               |
| Status      | `Status` (enum) | private     | Estado actual del usuario (activo, suspendido, eliminado) |

###### Tabla 19

_Tabla de métodos de User en el Domain Layer de IAM_

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                  |
|----------------|-----------------|-------------|----------------------------------------------|
| ChangeName     | `void`          | public      | 	Modifica el nombre completo del usuario     |
| ChangeEmail    | `void`          | public      | 	Actualiza el correo electrónico del usuario |
| ChangePassword | `void`          | public      | Cambia la contraseña del usuario             |
| ChangeRole     | `void`          | public      | Asigna nuevos roles al usuario               |
| Suspend        | `void`          | public      | 	Marca al usuario como suspendido            |
| Activate       | `void`          | public      | Reactiva a un usuario suspendido             |
| Delete         | `void`          | public      | Marca lógicamente al usuario como eliminado  |

**UserId**

###### Tabla 20

_Tabla de UserId en el Domain Layer de IAM_

| Propiedad     | Valor                                        |
|---------------|----------------------------------------------|
| **Nombre**    | UserId                                       |
| **Categoría** | Value Object                                 |
| **Propósito** | Encapsular el identificador único de usuario |

###### Tabla 21

_Tabla de atributos de UserId en el Domain Layer de IAM_

| Nombre | Tipo de dato | Visibilidad | Descripción                      |
|--------|--------------|-------------|----------------------------------|
| Value  | `Long`       | private     | Valor numérico del identificador |

**FullName**

###### Tabla 22

_Tabla de FullName en el Domain Layer de IAM_

| Propiedad     | Valor                                         |
|---------------|-----------------------------------------------|
| **Nombre**    | FullName                                      |
| **Categoría** | Value Object                                  |
| **Propósito** | 	Representar el nombre completo de un usuario |

###### Tabla 23

_Tabla de atributos de FullName en el Domain Layer de IAM_

| Nombre     | Tipo de dato | Visibilidad | Descripción               |
|------------|--------------|-------------|---------------------------|
| name       | `string`     | private     | Nombre del usuario        |
| LastNames  | `string`     | private     | Apellidos del usuario     |

**Email**

###### Tabla 24

_Tabla de Email en el Domain Layer de IAM_

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | Email                                     |
| **Categoría** | Value Object                              |
| **Propósito** | 	Representar un correo electrónico válido |

###### Tabla 25

_Tabla de atributos de Email en el Domain Layer de IAM_

| Nombre | Tipo de dato | Visibilidad | Descripción                     |
|--------|--------------|-------------|---------------------------------|
| Email  | `string`     | private     | Dirección de correo electrónico |

**PasswordHash**

###### Tabla 26

_Tabla de PasswordHash en el Domain Layer de IAM_

| Propiedad     | Valor                                                      |
|---------------|------------------------------------------------------------|
| **Nombre**    | PasswordHash                                               |
| **Categoría** | Value Object                                               |
| **Propósito** | 	Almacenar la versión en hash de la contraseña del usuario |

###### Tabla 27

_Tabla de atributos de PasswordHash en el Domain Layer de IAM_

| Nombre | Tipo de dato | Visibilidad | Descripción                       |
|--------|--------------|-------------|-----------------------------------|
| email  | `string`     | private     | Hash de la contraseña del usuario |

###### Tabla 28

_Tabla de métodos de PasswordHash en el Domain Layer de IAM_

| Nombre  | Tipo de retorno | Visibilidad | Descripción                                                               |
|---------|-----------------|-------------|---------------------------------------------------------------------------|
| Matches | `bool`          | public      | Verifica si una contraseña en texto plano coincide con el hash almacenado |

**UserFactory**

###### Tabla 29

_Tabla de UserFactory en el Domain Layer de IAM_

| Propiedad     | Valor                             |
|---------------|-----------------------------------|
| **Nombre**    | UserFactory                       |
| **Categoría** | Factory                           |
| **Propósito** | 	Crear instancias válidas de User |

###### Tabla 30

_Tabla de métodos de UserFactory en el Domain Layer de IAM_

| Nombre | Tipo de retorno | Visibilidad | Descripción                           |
|--------|-----------------|-------------|---------------------------------------|
| Create | `User`          | public      | Construye una nueva instancia de User |

**IUserRepository**

###### Tabla 31

_Tabla de IUserRepository en el Domain Layer de IAM_

| Propiedad     | Valor                                  |
|---------------|----------------------------------------|
| **Nombre**    | IUserRepository                        |
| **Categoría** | Repository                             |
| **Propósito** | Interfaz para persistencia de usuarios |

###### Tabla 32

_Tabla de métodos de IUserRepository en el Domain Layer de IAM_

| Nombre               | Tipo de retorno | Visibilidad | Descripción                                                        |
|----------------------|-----------------|-------------|--------------------------------------------------------------------|
| GetByIdAsync         | `User?`         | public      | Obtiene un usuario por su identificador                            |
| FindByEmailAsync     | `User?`         | public      | Busca un usuario por su correo electrónico                         |
| ExistsByEmailAsync   | `bool`          | public      | Verifica si un usuario ya está registrado con un email determinado |
| FindAllAsync         | `List<User>`    | public      | Recupera todos los usuarios registrados (uso administrativo)       |
| SaveAsync            | `User`          | public      | Persiste o actualiza un usuario                                    |
| DeleteLogicallyAsync | `bool`          | public      | Marca un usuario como eliminado lógicamente                        |
| CountAsync           | `long`          | public      | Devuelve el total de usuarios registrados                          |

**ISessionRepository**

###### Tabla 33

_Tabla de ISessionRepository en el Domain Layer de IAM_

| Propiedad     | Valor                                    |
|---------------|------------------------------------------|
| **Nombre**    | ISessionRepository                       |
| **Categoría** | Repository                               |
| **Propósito** | Interfaz para gestionar sesiones activas |

###### Tabla 34

_Tabla de métodos de ISessionRepository en el Domain Layer de IAM_

| Nombre                  | Tipo de retorno | Visibilidad | Descripción                                      |
|-------------------------|-----------------|-------------|--------------------------------------------------|
| FindByTokenId           | `SessionToken?` | public      | Recupera un token de sesión por su identificador |
| Store                   | `void`          | public      | Persiste un nuevo token de sesión                |
| Revoke                  | `void`          | public      | Revoca un token de sesión específico             |
| RevokeAllSessionForUser | `void`          | public      | Revoca todas las sesiones activas de un usuario  |

**Authenticator**

###### Tabla 35

_Tabla de Authenticator en el Domain Layer de IAM_

| Propiedad     | Valor                                           |
|---------------|-------------------------------------------------|
| **Nombre**    | Authenticator                                   |
| **Categoría** | Domain Service                                  |
| **Propósito** | Validar credenciales y generar tokens de sesión |

###### Tabla 36

_Tabla de métodos de Authenticator en el Domain Layer de IAM_

| Nombre       | Tipo de retorno | Visibilidad | Descripción                                              |
|--------------|-----------------|-------------|----------------------------------------------------------|
| authenticate | `SessionToken`  | public      | Autentica a un usuario y emite un token de sesión válido |

**SessionToken**

###### Tabla 37

_Tabla de SessionToken en el Domain Layer de IAM_

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | SessionToken                              |
| **Categoría** | Entity                                    |
| **Propósito** | Representar una sesión autenticada activa |

###### Tabla 38

_Tabla de métodos de SessionToken en el Domain Layer de IAM_

| Nombre    | Tipo de dato | Visibilidad | Descripción                          |
|-----------|--------------|-------------|--------------------------------------|
| TokenId   | `string`     | private     | Identificador único del token        |
| userId    | `UserId`     | private     | Identificador del usuario asociado   |
| createdAt | `DateTime`   | private     | Fecha y hora de creación del token   |
| expiresAt | `DateTime`   | private     | Fecha y hora de expiración del token |
| revoked   | `bool`       | private     | Indica si el token ha sido revocado  |

#### 4.2.1.2. IAM Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de IAM se exponen los endpoints necesarios para interactuar con las funcionalidades de autenticación, autorización y gestión de usuarios. A través de controladores especializados, esta capa actúa como punto de entrada para solicitudes externas, facilitando la comunicación entre clientes (como aplicaciones web o móviles) y la lógica de negocio. Su diseño busca garantizar una separación clara de responsabilidades, manteniendo la simplicidad en la orquestación de comandos y consultas sin comprometer la seguridad ni la escalabilidad del sistema.

**UserController**

###### Tabla 39

_Tabla de SessionToken en el Interface Layer de IAM_

| Propiedad     | Valor                                      |
|---------------|--------------------------------------------|
| **Nombre**    | UserController                             |
| **Categoría** | Controller                                 |
| **Propósito** | Exponer endpoints para gestión de usuarios |
| **Ruta**      | `/api/users`                               |

###### Tabla 40

_Tabla de métodos de SessionToken en el Interface Layer de IAM_

| Nombre         | Ruta                 | Acción                          | Handle                                                           |
|----------------|----------------------|---------------------------------|------------------------------------------------------------------|
| GetById        | `/{userId}`          | Obtiene los datos de un usuario | `GetUserByIdQuery`                                               |
| ChangeName     | `/{userId}/name`     | Cambia `FullName`               | `ChangeUserNameCommand`                                          |
| ChangeEmail    | `/{userId}/email`    | Cambia `Email`                  | `ChangeUserEmailCommand`                                         |
| ChangePassword | `/{userId}/password` | Cambia `PasswordHash`           | `ChangeUserPasswordCommand`                                      |
| ChangeStatus   | `/{userId}/status`   | Cambia `Status`                 | `ActivateUserCommand`, `SuspendUserCommand`, `DeleteUserCommand` |

**AuthController**

###### Tabla 41

_Tabla de AuthController en el Interface Layer de IAM_

| Propiedad     | Valor                                                                 |
|---------------|-----------------------------------------------------------------------|
| **Nombre**    | AuthController                                                        |
| **Categoría** | Controller                                                            |
| **Propósito** | Encargado de todo lo relacionado con registro y autenticación         |
| **Ruta**      | `/api/auth`                                                           |

###### Tabla 42

_Tabla de métodos de AuthController en el Interface Layer de IAM_

| Nombre   | Ruta         | Acción                                    | Handle                     |
|----------|--------------|-------------------------------------------|----------------------------|
| Register | `/register`  | Crea un nuevo usuario                     | `RegisterUserCommand`      |
| Login    | `/login`     | Valida credenciales y devuelve token      | `LoginUserCommand`         |
| Refresh  | `/refresh`   | Renueva el acceso; nuevo token            | `~`                        |
| Logout   | `/logout`    | Revoca el token activo                    | `RevokeSessionCommand`     |

#### 4.2.1.3. IAM Bounded Context Application Layer 

La capa de aplicación del Bounded Context de IAM coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin mezclar reglas de negocio. Aquí residen los Command Handlers, Query Handlers y Event Handlers, responsables de ejecutar operaciones como el registro, inicio o cierre de sesión, así como la gestión de eventos relacionados con la identidad de los usuarios. Esta capa asegura que las acciones se realicen de manera transaccional, manteniendo la integridad del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según corresponda.

**UserRegisterCommandHandler**

###### Tabla 43

_Tabla de UserRegisterCommandHandler en el Application Layer de IAM_

| Propiedad     | Valor                      |
|---------------|----------------------------|
| **Nombre**    | UserRegisterCommandHandler |
| **Categoría** | Command Handler            |
| **Propósito** | Registrar un usuario       |
| **Comando**   | RegisterUserCommand        |

**UserLoginCommandHandler**

###### Tabla 44

_Tabla de UserLoginCommandHandler en el Application Layer de IAM_

| Propiedad     | Valor                       |
|---------------|-----------------------------|
| **Nombre**    | UserLoginCommandHandler     |
| **Categoría** | Command Handler             |
| **Propósito** | Iniciar sesión a un usuario |
| **Comando**   | LoginUserCommand            |

**UserLogoutCommandHandler**

###### Tabla 45

_Tabla de UserLogoutCommandHandler en el Application Layer de IAM_

| Propiedad     | Valor                       |
|---------------|-----------------------------|
| **Nombre**    | UserLogoutCommandHandler    |
| **Categoría** | Command Handler             |
| **Propósito** | Cerrar sesión de un usuario |
| **Comando**   | LogoutUserCommand           |

**RegisteredUserEventHandler**

###### Tabla 46

_Tabla de RegisteredUserEventHandler en el Application Layer de IAM_

| Propiedad     | Valor                               |
|---------------|-------------------------------------|
| **Nombre**    | RegisteredUserEventHandler          |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserRegisteredEvent                 |

**UserLoggedInEventHandler**

###### Tabla 47

_Tabla de UserLoggedInEventHandler en el Application Layer de IAM_

| Propiedad     | Valor                               |
|---------------|-------------------------------------|
| **Nombre**    | UserLoggedInEventHandler            |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserLoggedInEvent                   |

**UserLoggedOutEventHandler**

###### Tabla 48

_Tabla de UserLoggedOutEventHandler en el Application Layer de IAM_

| Propiedad     | Valor                               |
|---------------|-------------------------------------|
| **Nombre**    | UserLoggedOutEventHandler           |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserLoggedOutEvent                  |

#### 4.2.1.4. Infrastructure Layer

La capa de infraestructura del Bounded Context de IAM actúa como el puente entre la lógica de negocio y los mecanismos técnicos de persistencia, comunicación y ejecución. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, proveedores de autenticación, mecanismos de almacenamiento de sesiones y otros servicios externos o compartidos.

Esta capa concreta las abstracciones definidas en el dominio mediante implementaciones de repositorios. Su diseño busca mantener el desacoplamiento respecto a la lógica central, permitiendo la evolución tecnológica sin comprometer la integridad del dominio. Además, garantiza la eficiencia, seguridad y confiabilidad en la gestión de identidades, roles y sesiones, alineándose con los objetivos funcionales y no funcionales del sistema.

**UserRepository**

###### Tabla 49

_Tabla de UserRepository en el Infraestructure Layer de IAM_

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | UserRepository                            |
| **Categoría** | Repositorio                               |
| **Propósito** | Persistir y consultar entidades de `User` |
| **Interfaz**  | `IUserRepository`                         |

**SessionRepository**

###### Tabla 50

_Tabla de SessionRepository en el Infraestructure Layer de IAM_

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | SessionRepository                         |
| **Categoría** | Repositorio                               |
| **Propósito** | Persistir y consultar entidades de `User` |
| **Interfaz**  | `ISessionRepository`                      |

**AppDbContext**

###### Tabla 51

_Tabla de AppDbContext en el Infraestructure Layer de IAM_

| Propiedad     | Valor                                          |
|---------------|------------------------------------------------|
| **Nombre**    | AppDbContext                                   |
| **Categoría** | ORM Context                                    |
| **Propósito** | Punto central de acceso a la base de datos     |

#### 4.2.1.5. IAM Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de IAM. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales del contexto de gestión de identidad y acceso.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y seguridad del sistema.

###### Figura 80
*Participación del Bounded Context de IAM con la aplicación móvil mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-IAM-MobileComponent.png"></image>

###### Figura 81
*Participación del Bounded Context de IAM con la aplicación web mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-IAM-WebComponent.png"></image>

###### Figura 82
*Participación del Bounded Context de IAM con la Cloud API mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-IAM-APIComponent.png"></image>

#### 4.2.1.6. IAM Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de IAM, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 4.2.1.6.1. IAM Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de IAM. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica de dominio, así como sus relaciones fundamentales. El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y su rol dentro del modelo.

Asimismo, se incluyen las relaciones entre elementos del dominio, calificadas con nombres descriptivos, direccionalidad —cuando corresponde— y multiplicidad para reflejar con precisión el grado de asociación entre las entidades. Esta vista detallada del diseño táctico favorece la comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación efectiva dentro de la arquitectura de software.

###### Figura 83
*Diagrama de clases de la capa de dominio del Bounded Context de IAM*

<image src="../assets/img/capitulo-4/bounded-context-iam/class-diagram.png"></image>

##### 4.2.1.6.2. IAM Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de IAM. Esta representación permite visualizar de forma estructurada y precisa las clases, interfaces y enumeraciones que conforman la lógica de dominio, junto con sus atributos, métodos y responsabilidades específicas dentro del modelo.

El diagrama incluye detalles esenciales como el tipo de dato y la visibilidad de cada miembro, así como las relaciones entre los distintos elementos del dominio. Estas relaciones están calificadas con nombres descriptivos, indican la dirección cuando aplica, e incorporan multiplicidades para representar con fidelidad la cardinalidad de cada asociación.

Esta visualización detallada contribuye significativamente a la comprensión compartida del modelo conceptual, funcionando como un nexo clave entre el análisis de dominio y su posterior implementación en la arquitectura del sistema.

###### Figura 84
*Diagrama de base de datos del Bounded Context de IAM*

<image src="../assets/img/capitulo-4/bounded-context-iam/database-diagram.png"></image>

### 4.2.2. Bounded Context: Profile and Preferences

En el contexto táctico, el Bounded Context Profiles and Preferences concentra toda la funcionalidad relacionada con la gestión personalizada de los perfiles de usuario en la plataforma Macetech. Este módulo se encarga de almacenar, actualizar y exponer información detallada sobre las preferencias individuales, hábitos de uso, configuraciones personalizadas y características del entorno del usuario. Entre sus responsabilidades se incluyen la edición de datos personales no sensibles, la gestión de configuraciones del dispositivo vinculado (como idioma, notificaciones o zonas horarias), y la persistencia de hábitos o preferencias en el cuidado de plantas.

Profiles and Preferences permite adaptar la experiencia digital a las necesidades particulares de cada usuario, y lo hace mediante una interfaz limpia e interoperable, disponible para otros bounded contexts. Al ofrecer un punto centralizado para el perfilado y la personalización, garantiza consistencia, reutilización y separación de preocupaciones dentro de la arquitectura de la solución.

#### 4.2.2.1. Profile and Preferences Bounded Context Domain Layer

En la capa de dominio de Profiles and Preferences se modelan las entidades, objetos de valor y reglas de negocio fundamentales asociadas a la gestión de perfiles y preferencias personalizadas. Esta capa encapsula la lógica central vinculada al almacenamiento, validación y actualización de datos relacionados con la configuración del usuario, sus preferencias de uso y hábitos de interacción con la plataforma. Asimismo, se definen los Domain Services responsables de coordinar operaciones complejas que involucran múltiples objetos, asegurando la coherencia del comportamiento del sistema y promoviendo su reutilización en otros contextos.

**Profile**

###### Tabla 52

_Tabla de Profile en el Domain Layer de Profile and Preferences_

| Propiedad     | Valor                                                              |
|---------------|--------------------------------------------------------------------|
| **Nombre**    | Profile                                                            |
| **Categoría** | Aggregate Root                                                     |
| **Propósito** | Agrupar y gestionar los datos de perfil y personales de un usuario |

###### Tabla 53

_Tabla de atributos de Profile en el Domain Layer de Profile and Preferences_

| Nombre           | Tipo de dato    | Visibilidad | Descripción                                         |
|------------------|-----------------|-------------|-----------------------------------------------------|
| userUid          | `String`        | private     | Identificador único del usuario                     |
| name             | `FullName`      | private     | Nombre completo del usuario                         |
| phoneNumber      | `PhoneNumber`   | private     | Número de teléfono del usuario                      |
| streetAddress    | `StreetAddress` | private     | Dirección física del usuario                        |
| profileRole      | `ProfileRole`   | private     | Rol asignado al perfil (Amateur o Gardener)         |
| imageUrl         | `String`        | private     | URL de la imagen de perfil                          |
| notifyUsingEmail | `Boolean`       | private     | Indica si el usuario desea notificaciones por email |
| createdAt        | `DateTime`      | private     | Fecha de creación del perfil                        |
| updatedAt        | `DateTime`      | private     | Fecha de la última actualización del perfil         |

###### Tabla 54

_Tabla de métodos de Profile en el Domain Layer de Profile and Preferences_

| Nombre                  | Tipo de retorno | Visibilidad | Descripción                                             |
|-------------------------|-----------------|-------------|---------------------------------------------------------|
| changeName              | `void`          | public      | Actualiza el `name` y marca `updatedAt`                 |
| changePhoneNumber       | `void`          | public      | Actualiza el `phoneNumber` y marca `updatedAt`          |
| changeStreetAddress     | `void`          | public      | Actualiza el `streetAddress` y marca `updatedAt`        |
| setProfileImage         | `void`          | public      | Actualiza el `imageUrl` y marca `updatedAt`             |
| toggleEmailNotification | `void`          | public      | Activa/desactiva `notifyUsingEmail` y marca `updatedAt` |
| markUpdated             | `void`          | private     | Actualiza internamente el campo `updatedAt`             |

**FullName**

###### Tabla 55

_Tabla de FullName en el Domain Layer de Profile and Preferences_

| Propiedad     | Valor                                    |
|---------------|------------------------------------------|
| **Nombre**    | FullName                                 |
| **Categoría** | Value Object                             |
| **Propósito** | Encapsular nombre y apellido del usuario |

###### Tabla 56

_Tabla de atributos de FullName en el Domain Layer de Profile and Preferences_

| Nombre   | Tipo de dato | Visibilidad | Descripción           |
|----------|--------------|-------------|-----------------------|
| name     | `String`     | private     | Nombre propio         |
| lastName | `String`     | private     | Apellidos del usuario |

###### Tabla 57

_Tabla de métodos de FullName en el Domain Layer de Profile and Preferences_

| Nombre   | Tipo de retorno | Visibilidad | Descripción                     |
|----------|-----------------|-------------|---------------------------------|
| fullName | `String`        | public      | Retorna `name + " " + lastName` |

**PhoneNumber**

###### Tabla 58

_Tabla de PhoneNumber en el Domain Layer de Profile and Preferences_

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | PhoneNumber                               |
| **Categoría** | Value Object                              |
| **Propósito** | Validar y almacenar un número de teléfono |

###### Tabla 59

_Tabla de atributos de PhoneNumber en el Domain Layer de Profile and Preferences_

| Nombre      | Tipo de dato | Visibilidad | Descripción                |
|-------------|--------------|-------------|----------------------------|
| countryCode | `String`     | private     | Código de país (ej. "+51") |
| number      | `String`     | private     | Número local del teléfono  |

###### Tabla 60

_Tabla de métodos de PhoneNumber en el Domain Layer de Profile and Preferences_

| Nombre    | Tipo de retorno | Visibilidad | Descripción                     |
|-----------|-----------------|-------------|---------------------------------|
| formatted | `String`        | public      | Devuelve `countryCode + number` |

**StreetAddress**

###### Tabla 61

_Tabla de StreetAddress en el Domain Layer de Profile and Preferences_

| Propiedad     | Valor                                  |
|---------------|----------------------------------------|
| **Nombre**    | StreetAddress                          |
| **Categoría** | Value Object                           |
| **Propósito** | Almacenar datos de la dirección física |

###### Tabla 62

_Tabla de atributos de StreetAddress en el Domain Layer de Profile and Preferences_

| Nombre       | Tipo de dato | Visibilidad | Descripción                        |
|--------------|--------------|-------------|------------------------------------|
| street       | `String`     | private     | Nombre de la calle                 |
| streetNumber | `String`     | private     | Número o identificador de la calle |
| city         | `String`     | private     | Ciudad                             |
| postalCode   | `String`     | private     | Código postal                      |
| country      | `String`     | private     | País                               |

###### Tabla 63

_Tabla de métodos de StreetAddress en el Domain Layer de Profile and Preferences_

| Nombre      | Tipo de retorno | Visibilidad | Descripción                                               |
|-------------|-----------------|-------------|-----------------------------------------------------------|
| fullAddress | `String`        | public      | Retorna la concatenación de todos los campos de dirección |

**ProfileRole**

###### Tabla 64

_Tabla de ProfileRole en el Domain Layer de Profile and Preferences_

| Propiedad     | Valor                                   |
|---------------|-----------------------------------------|
| **Nombre**    | ProfileRole                             |
| **Categoría** | Enum                                    |
| **Propósito** | Definir los posibles roles de un perfil |

###### Tabla 65

_Tabla de valores de ProfileRole en el Domain Layer de Profile and Preferences_

| Valor    | Descripción                 |
|----------|-----------------------------|
| Amateur  | Perfil de usuario amateur   |
| Gardener | Perfil de usuario jardinero |

**ProfileFactory**

###### Tabla 66

_Tabla de ProfileFactory en el Domain Layer de Profile and Preferences_

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | ProfileFactory                            |
| **Categoría** | Factory                                   |
| **Propósito** | Construir instancias válidas de `Profile` |

###### Tabla 67

_Tabla de métodos de ProfileFactory en el Domain Layer de Profile and Preferences_

| Nombre | Tipo de retorno | Visibilidad | Descripción                                                                                       |
|--------|-----------------|-------------|---------------------------------------------------------------------------------------------------|
| create | `Profile`       | public      | Crea un `Profile` a partir de datos primitivos, valida valores y asigna `createdAt` y `updatedAt` |

## IProfileRepository

###### Tabla 68

_Tabla de IProfileFactory en el Domain Layer de Profile and Preferences_

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | IProfileRepository                        |
| **Categoría** | Repository                                |
| **Propósito** | Persistir y recuperar entidades `Profile` |

###### Tabla 69

_Tabla de métodos de IProfileFactory en el Domain Layer de Profile and Preferences_

| Nombre        | Tipo de retorno | Visibilidad | Descripción                                       |
|---------------|-----------------|-------------|---------------------------------------------------|
| findById      | `Profile?`      | public      | Recupera un perfil según su identificador interno |
| findByUserUid | `Profile?`      | public      | Recupera un perfil según `userUid`                |
| create        | `Unit`          | public      | Persiste un nuevo `Profile`                       |
| update        | `Unit`          | public      | Actualiza un `Profile` existente                  |
| delete        | `Unit`          | public      | Elimina lógicamente un `Profile`                  |

#### 4.2.2.2. Profile and Preferences Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Profiles and Preferences se exponen los endpoints necesarios para gestionar la información de perfil de usuario y sus preferencias personalizadas dentro de la plataforma Macetech. A través de controladores dedicados, esta capa actúa como intermediaria entre las aplicaciones cliente y la lógica de negocio, permitiendo operaciones como la visualización, edición y actualización de datos personales y configuraciones. Su diseño promueve una arquitectura desacoplada y segura, enfocada en mantener una experiencia fluida y adaptable para el usuario sin comprometer la coherencia del sistema.

**ProfileController**

###### Tabla 70

_Tabla de ProfileController en el Interface Layer de Profile and Preferences_

| Propiedad     | Valor                             |
|---------------|-----------------------------------|
| **Nombre**    | ProfileController                 |
| **Categoría** | Controller                        |
| **Propósito** | Exponer servicios REST de Profile |
| **Ruta**      | `/api/profile/`                   |

###### Tabla 71

_Tabla de métodos de ProfileController en el Interface Layer de Profile and Preferences_

| Nombre                   | Ruta                 | Acción                     | Handle                            |
|--------------------------|----------------------|----------------------------|-----------------------------------|
| getProfile               | `/{uid}`             | Obtener perfil             | `GetProfileQuery`                 |
| updateProfile            | `/{uid}`             | Actualizar perfil completo | `UpdateProfileCommand`            |
| deleteProfile            | `/{uid}`             | Eliminar perfil            | `DeleteProfileCommand`            |
| createProfile            | `/create`            | Crear nuevo perfil         | `CreateProfileCommand`            |
| updateProfilePreferences | `/preferences/{uid}` | Actualizar preferencias    | `UpdateProfilePreferencesCommand` |

#### 4.2.2.3. Profile and Preferences Bounded Context Application Layer

La capa de aplicación del Bounded Context de Profiles and Preferences coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se implementan los Command Handlers, Query Handlers y Event Handlers responsables de operaciones como la edición de información personal, actualización de preferencias del usuario y notificación de cambios relevantes. Su rol es garantizar que dichas acciones se ejecuten de forma consistente y transaccional, delegando la lógica central al dominio y apoyándose en la infraestructura cuando sea necesario, manteniendo así la cohesión funcional del sistema.

**GetProfileQueryHandler**

###### Tabla 72

_Tabla de ProfileQueryHandler en el Application Layer de Profile and Preferences_

| Propiedad     | Valor                                    |
|---------------|------------------------------------------|
| **Nombre**    | GetProfileQueryHandler                   |
| **Categoría** | Query Handler                            |
| **Propósito** | Manejar la lógica para `GetProfileQuery` |

**CreateProfileCommandHandler**

###### Tabla 73

_Tabla de CreateProfileCommandHandler en el Application Layer de Profile and Preferences_

| Propiedad     | Valor                                                      |
|---------------|------------------------------------------------------------|
| **Nombre**    | CreateProfileCommandHandler                                |
| **Categoría** | Command Handler                                            |
| **Propósito** | Ejecutar la creación de un perfil (`CreateProfileCommand`) |

**UpdateProfileCommandHandler**

###### Tabla 74

_Tabla de UpdateProfileCommandHandler en el Application Layer de Profile and Preferences_

| Propiedad     | Valor                                                           |
|---------------|-----------------------------------------------------------------|
| **Nombre**    | UpdateProfileCommandHandler                                     |
| **Categoría** | Command Handler                                                 |
| **Propósito** | Ejecutar la actualización de un perfil (`UpdateProfileCommand`) |

**DeleteProfileCommandHandler**

###### Tabla 75

_Tabla de DeleteProfileCommandHandler en el Application Layer de Profile and Preferences_

| Propiedad     | Valor                                                         |
|---------------|---------------------------------------------------------------|
| **Nombre**    | DeleteProfileCommandHandler                                   |
| **Categoría** | Command Handler                                               |
| **Propósito** | Ejecutar la eliminación de un perfil (`DeleteProfileCommand`) |

**UpdateProfilePreferencesCommandHandler**

###### Tabla 76

_Tabla de UpdateProfilePreferencesCommandHandler en el Application Layer de Profile and Preferences_

| Propiedad     | Valor                                                                                   |
|---------------|-----------------------------------------------------------------------------------------|
| **Nombre**    | UpdateProfilePreferencesCommandHandler                                                  |
| **Categoría** | Command Handler                                                                         |
| **Propósito** | Ejecutar la actualización de preferencias de perfil (`UpdateProfilePreferencesCommand`) |

**CreatedProfileEventHandler**

###### Tabla 77

_Tabla de CreatedProfileEventHandler en el Application Layer de Profile and Preferences_

| Propiedad     | Valor                                                   |
|---------------|---------------------------------------------------------|
| **Nombre**    | CreatedProfileEventHandler                              |
| **Categoría** | Event Handler                                           |
| **Propósito** | Procesar la lógica tras el evento `ProfileCreatedEvent` |

**UpdatedProfileEventHandler**

###### Tabla 78

_Tabla de UpdatedProfileEventHandler en el Application Layer de Profile and Preferences_

| Propiedad     | Valor                                                   |
|---------------|---------------------------------------------------------|
| **Nombre**    | UpdatedProfileEventHandler                              |
| **Categoría** | Event Handler                                           |
| **Propósito** | Procesar la lógica tras el evento `ProfileUpdatedEvent` |

**DeletedProfileEventHandler**

###### Tabla 79

_Tabla de DeletedProfileEventHandler en el Application Layer de Profile and Preferences_

| Propiedad     | Valor                                                   |
|---------------|---------------------------------------------------------|
| **Nombre**    | DeletedProfileEventHandler                              |
| **Categoría** | Event Handler                                           |
| **Propósito** | Procesar la lógica tras el evento `ProfileDeletedEvent` |

#### 4.2.2.4. Profile and Preferences Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Profile and Preferences sirve como enlace entre la lógica de negocio y los mecanismos técnicos que permiten la persistencia y comunicación con recursos externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, servicios de almacenamiento y otros módulos relevantes que permiten gestionar la información de perfil y preferencias de los usuarios.

Esta capa materializa las abstracciones definidas en el dominio mediante la implementación de repositorios y adaptadores técnicos. Su diseño favorece el desacoplamiento de la lógica central, facilitando la evolución tecnológica sin afectar la integridad del modelo. Asimismo, asegura una gestión consistente, eficiente y segura de los datos personales, configuraciones y preferencias del usuario, en línea con los objetivos funcionales y no funcionales del sistema.

**ProfileRepository**

###### Tabla 80

_Tabla de ProfileRepository en el Infraestructure Layer de Profile and Preferences_

| Propiedad     | Valor                                                  |
|---------------|--------------------------------------------------------|
| **Nombre**    | ProfileRepository                                      |
| **Categoría** | Repository Implementation                              |
| **Propósito** | Implementar `IProfileRepository` usando ORM relacional |
| **Interfaz**  | `IProfileRepository`                                   |

#### 4.2.2.5. Profile and Preferences Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Profiles and Preferences. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías utilizadas y las interacciones entre ellos. Esta representación es fundamental para comprender en detalle cómo se organiza internamente cada parte del sistema, qué funcionalidades asume cada componente, y de qué manera colaboran para gestionar la información personal, preferencias y configuración personalizada del usuario dentro de Macetech.

Tal como establece el C4 Model, el nivel de componentes representa el cuarto nivel de abstracción en la visualización de arquitecturas de software, y resulta especialmente útil para desarrolladores y arquitectos al ofrecer una visión clara de las decisiones de diseño adoptadas en cada contenedor (Brown, 2023). Este nivel facilita la trazabilidad entre los elementos de alto nivel y su implementación específica, fortaleciendo la mantenibilidad, extensibilidad y coherencia del sistema.

###### Figura 85
*Participación del Bounded Context de Profile and Preferences con la aplicación móvil mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Profile-MobileComponent.png"></image>

###### Figura 86
*Participación del Bounded Context de Profile and Preferences con la aplicación web mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Profile-WebComponent.png"></image>

###### Figura 87
*Participación del Bounded Context de Profile and Preferences con la Cloud API mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Profile-APIComponent.png"></image>

#### 4.2.2.6. Profile and Preferences Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Profiles and Preferences, presentando diagramas que permiten visualizar con mayor precisión la estructura y composición de sus componentes clave. A través de representaciones estructuradas —como los diagramas de clases de la capa de dominio y el diagrama de base de datos— se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos del sistema que gestionan la configuración del perfil de usuario, sus intereses, preferencias y datos personales.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico y la implementación concreta. Esta aproximación garantiza que las decisiones tomadas a nivel táctico se materialicen en estructuras coherentes, sólidas y alineadas con los objetivos funcionales del contexto, brindando claridad y sostenibilidad al proceso de desarrollo y evolución del sistema.

##### 4.2.2.6.1. Profile and Preferences Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Profiles and Preferences. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que componen la lógica de dominio relacionada con la gestión del perfil del usuario, sus intereses, configuraciones personalizadas y preferencias de interacción dentro del ecosistema de Macetech.

El nivel de detalle incluye la definición de atributos y métodos para cada clase, especificando sus tipos de datos, visibilidad y rol dentro del modelo, así como las relaciones fundamentales entre los distintos elementos del dominio. Estas relaciones se representan con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, lo que permite reflejar con precisión el grado de asociación entre las entidades. Esta vista detallada facilita una comprensión común del modelo conceptual, sirviendo como puente entre el diseño del dominio y su posterior implementación técnica.

###### Figura 88
*Diagrama de clases de la capa de dominio del Bounded Context de Profile and Preferences*

<image src="../assets/img/capitulo-4/bounded-context-profile-and-personal-data/class-diagram-profile-and-personal-data.png"></image>

##### 4.2.2.6.2. Profile and Preferences Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Profiles and Preferences. Esta representación estructurada permite visualizar con claridad las entidades persistentes asociadas a la gestión de perfiles, intereses y preferencias del usuario, junto con sus atributos clave, tipos de datos, claves primarias y foráneas, y restricciones asociadas.

El diagrama refleja las relaciones entre las distintas tablas o entidades, indicando la dirección de las asociaciones, su naturaleza (uno a uno, uno a muchos, muchos a muchos) y la cardinalidad, lo que facilita el entendimiento de la estructura lógica que respalda el almacenamiento y la recuperación eficiente de datos dentro de este contexto.

Esta visualización resulta esencial para asegurar la coherencia entre el modelo conceptual y su implementación en la capa de persistencia, contribuyendo a una arquitectura sólida, escalable y alineada con los requerimientos funcionales y no funcionales del sistema.

###### Figura 89
*Diagrama de base de datos del Bounded Context de Profile and Preferences*

<image src="../assets/img/capitulo-4/bounded-context-profile-and-personal-data/database-diagram-profile-and-personal-data.png"></image>

### 4.2.3. Bounded Context: Asset & Resource Management

En el contexto táctico, el Bounded Context Asset & Resource Management agrupa toda la funcionalidad vinculada a la administración de activos físicos y recursos operativos dentro del ecosistema Macetech. Este módulo se encarga del registro, monitoreo y mantenimiento de los dispositivos IoT desplegados (como sensores de humedad, temperatura, pH, entre otros), permitiendo llevar un control detallado de su estado, ubicación, historial de intervenciones y condiciones operativas.

Asset & Resource Management centraliza el ciclo de vida de cada dispositivo, desde su activación inicial hasta su posible retiro o sustitución, asegurando trazabilidad completa y continuidad en la gestión técnica. Asimismo, incorpora mecanismos para la asignación de recursos a usuarios o entornos específicos, facilitando una administración eficiente y contextualizada. Este bounded context expone interfaces estandarizadas para permitir su integración con otros contextos funcionales, y actúa como fuente confiable de verdad sobre los activos tecnológicos desplegados en la plataforma.

#### 4.2.3.1. Asset & Resource Management Bounded Context Domain Layer

En la capa de dominio de Asset & Resource Management se definen las entidades y objetos de valor fundamentales relacionados con los activos físicos y digitales gestionados por Macetech, como sensores, macetas inteligentes y otros dispositivos IoT. Esta capa encapsula las reglas de negocio que regulan su ciclo de vida: desde el registro, asignación y mantenimiento, hasta su retiro o reemplazo. Además, en este nivel se ubican los Domain Services encargados de orquestar procesos complejos, como la vinculación entre usuarios y dispositivos o la planificación de recursos, asegurando coherencia, integridad y reutilización de la lógica central.

**Pot**

###### Tabla 81

_Tabla de Pot en el Domain Layer de Asset & Resource Management_

| Propiedad     | Valor                                                          |
|---------------|----------------------------------------------------------------|
| **Nombre**    | Pot                                                            |
| **Categoría** | Aggregate Root                                                 |
| **Propósito** | Representar una maceta con su ciclo de vida, estado y sensores |

###### Tabla 82

_Tabla de atributos de Pot en el Domain Layer de Asset & Resource Management_

| Nombre      | Tipo de dato | Visibilidad | Descripción                             |
|-------------|--------------|-------------|-----------------------------------------|
| id          | `Long`       | private     | Identificador único de la maceta        |
| userUid     | `String`     | private     | Identificador del usuario dueño         |
| tag         | `String`     | private     | Etiqueta o nombre amigable de la maceta |
| status      | `PotStatus`  | private     | Estado actual de la maceta              |
| humidity    | `Sensor`     | private     | Sensor de humedad asociado              |
| temperature | `Sensor`     | private     | Sensor de temperatura asociado          |
| water       | `Sensor`     | private     | Sensor de nivel de agua asociado        |

###### Tabla 83

_Tabla de métodos de Pot en el Domain Layer de Asset & Resource Management_

| Nombre            | Tipo de retorno | Visibilidad | Descripción                                    |
|-------------------|-----------------|-------------|------------------------------------------------|
| changeTag         | `void`          | public      | Actualiza la `tag` de la maceta                |
| changeStatus      | `void`          | public      | Actualiza el `status` de la maceta             |
| recordHumidity    | `void`          | public      | Actualiza el valor del sensor de `humidity`    |
| recordTemperature | `void`          | public      | Actualiza el valor del sensor de `temperature` |
| recordWaterLevel  | `void`          | public      | Actualiza el valor del sensor de `water`       |

**Group**

###### Tabla 84

_Tabla de Group en el Domain Layer de Asset & Resource Management_

| Propiedad     | Valor                                       |
|---------------|---------------------------------------------|
| **Nombre**    | Group                                       |
| **Categoría** | Entity                                      |
| **Propósito** | Agrupar varias macetas bajo un nombre común |

###### Tabla 85

_Tabla de atributos de Group en el Domain Layer de Asset & Resource Management_

| Nombre  | Tipo de dato | Visibilidad | Descripción                                     |
|---------|--------------|-------------|-------------------------------------------------|
| id      | `Long`       | private     | Identificador único del grupo                   |
| name    | `String`     | private     | Nombre del grupo                                |
| userUid | `String`     | private     | Identificador del usuario que creó el grupo     |
| potUid  | `List<Long>` | private     | Lista de IDs de macetas pertenecientes al grupo |

###### Tabla 86

_Tabla de métodos de Group en el Domain Layer de Asset & Resource Management_

| Nombre      | Tipo de retorno | Visibilidad | Descripción                         |
|-------------|-----------------|-------------|-------------------------------------|
| renameGroup | `void`          | public      | Cambia el nombre del grupo          |
| addPot      | `void`          | public      | Añade un ID de maceta a `potUid`    |
| removePot   | `void`          | public      | Elimina un ID de maceta de `potUid` |

**Sensor**

###### Tabla 87

_Tabla de Sensor en el Domain Layer de Asset & Resource Management_

| Propiedad     | Valor                                               |
|---------------|-----------------------------------------------------|
| **Nombre**    | Sensor                                              |
| **Categoría** | Value Object                                        |
| **Propósito** | Representar la lectura y estado de un sensor físico |

###### Tabla 88

_Tabla de atributos de Sensor en el Domain Layer de Asset & Resource Management_

| Nombre           | Tipo de dato | Visibilidad | Descripción                                               |
|------------------|--------------|-------------|-----------------------------------------------------------|
| value            | `Float`      | private     | Valor actual de la medición                               |
| isMalfunctioning | `Boolean`    | private     | Indica si el sensor está fallando                         |
| measurementType  | `String`     | private     | Tipo de medición (ej. "humidity", "temperature", "water") |

###### Tabla 89

_Tabla de métodos de Sensor en el Domain Layer de Asset & Resource Management_

| Nombre           | Tipo de retorno | Visibilidad | Descripción                             |
|------------------|-----------------|-------------|-----------------------------------------|
| updateValue      | `void`          | public      | Asigna un nuevo `value`                 |
| markMalfunction  | `void`          | public      | Marca el sensor como en fallo           |
| clearMalfunction | `void`          | public      | Restablece `isMalfunctioning` a `false` |

**PotStatus**

###### Tabla 90

_Tabla de PotStatus en el Domain Layer de Asset & Resource Management_

| Propiedad     | Valor                                      |
|---------------|--------------------------------------------|
| **Nombre**    | PotStatus                                  |
| **Categoría** | Enum                                       |
| **Propósito** | Definir los posibles estados de una maceta |

###### Tabla 91

_Tabla de valores de PotStatus en el Domain Layer de Asset & Resource Management_

| Valor    | Descripción |
|----------|-------------|
| Free     | Disponible  |
| InUse    | En uso      |
| Inactive | Inactiva    |
| Broken   | Dañada      |

**PotFactory**

###### Tabla 92

_Tabla de PotFactory en el Domain Layer de Asset & Resource Management_

| Propiedad     | Valor                                    |
|---------------|------------------------------------------|
| **Nombre**    | PotFactory                               |
| **Categoría** | Factory                                  |
| **Propósito** | Crear nuevas instancias válidas de `Pot` |

###### Tabla 93

_Tabla de métodos de PotFactory en el Domain Layer de Asset & Resource Management_

| Nombre | Tipo de retorno | Visibilidad | Descripción                                                                         |
|--------|-----------------|-------------|-------------------------------------------------------------------------------------|
| create | `Pot`           | public      | Construye un `Pot` inicializando `id`, `userUid`, `tag`, `status` y sensores vacíos |

**IPotRepository**

###### Tabla 94

_Tabla de IPotRepository en el Domain Layer de Asset & Resource Management_

| Propiedad     | Valor                                 |
|---------------|---------------------------------------|
| **Nombre**    | IPotRepository                        |
| **Categoría** | Repository                            |
| **Propósito** | Persistir y recuperar entidades `Pot` |

###### Tabla 95

_Tabla de métodos de IPotRepository en el Domain Layer de Asset & Resource Management_

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                     |
|----------------|-----------------|-------------|-------------------------------------------------|
| findById       | `Pot?`          | public      | Recupera un `Pot` por su `id`                   |
| findByUserUid  | `List<Pot>`     | public      | Recupera todas las macetas de un usuario        |
| findByGroupUid | `List<Pot>`     | public      | Recupera todas las macetas asociadas a un grupo |
| findByTag      | `Pot?`          | public      | Busca una maceta por su `tag`                   |
| update         | `Unit`          | public      | Actualiza un `Pot` existente                    |
| create         | `Unit`          | public      | Persiste un nuevo `Pot`                         |

**IGroupRepository**

###### Tabla 96

_Tabla de IGroupRepository en el Domain Layer de Asset & Resource Management_

| Propiedad     | Valor                                   |
|---------------|-----------------------------------------|
| **Nombre**    | IGroupRepository                        |
| **Categoría** | Repository                              |
| **Propósito** | Persistir y recuperar entidades `Group` |

###### Tabla 97

_Tabla de métodos de IGroupRepository en el Domain Layer de Asset & Resource Management_

| Nombre        | Tipo de retorno | Visibilidad | Descripción                                        |
|---------------|-----------------|-------------|----------------------------------------------------|
| findById      | `Group?`        | public      | Recupera un `Group` por su `id`                    |
| findByUserUid | `List<Group>`   | public      | Recupera todos los grupos de un usuario            |
| findByPotUid  | `List<Group>`   | public      | Recupera todos los grupos que contienen una maceta |
| update        | `Unit`          | public      | Actualiza un `Group` existente                     |
| create        | `Unit`          | public      | Persiste un nuevo `Group`                          |
| delete        | `Unit`          | public      | Elimina un `Group`                                 |

#### 4.2.3.2. Asset & Resource Management Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Asset & Resource Management se exponen los endpoints necesarios para gestionar la infraestructura física y digital asociada a los dispositivos inteligentes de Macetech. Su diseño promueve una separación clara de responsabilidades, orquestando de forma eficiente comandos y consultas, al tiempo que garantiza trazabilidad, disponibilidad y consistencia de los recursos gestionados.

**PotController**

###### Tabla 98

_Tabla de PotController en el Interface Layer de Asset & Resource Management_

| Propiedad     | Valor                                    |
|---------------|------------------------------------------|
| **Nombre**    | PotController                            |
| **Categoría** | Controller                               |
| **Propósito** | Exponer API REST para gestión de macetas |
| **Ruta**      | `/api/pot/`                              |

###### Tabla 99

_Tabla de métodos de PotController en el Interface Layer de Asset & Resource Management_

| Nombre            | Ruta                 | Acción                                  | Handle                   |
|-------------------|----------------------|-----------------------------------------|--------------------------|
| getPot            | `/{id}`              | Obtener una maceta por ID               | `GetPotQuery`            |
| getAllPots        | `/all/{userId}`      | Obtener todas las macetas de un usuario | `GetAllPotsQuery`        |
| getAllPotsByGroup | `/group/{groupId}`   | Obtener macetas de un grupo             | `GetAllPotsByGroupQuery` |
| updatePot         | `/{id}`              | Actualizar datos de una maceta          | `UpdatePotCommand`       |
| linkPot           | `/link-user/{id}`    | Enlazar maceta a un usuario             | `LinkPotCommand`         |
| unlinkPot         | `/unlink-user/{id}`  | Desenlazar maceta de un usuario         | `UnlinkPotCommand`       |
| assignPlant       | `/assign-plant/{id}` | Asignar planta a una maceta             | `AssignPlantCommand`     |

**GroupController**

###### Tabla 100

_Tabla de GroupController en el Interface Layer de Asset & Resource Management_

| Propiedad     | Valor                                   |
|---------------|-----------------------------------------|
| **Nombre**    | GroupController                         |
| **Categoría** | Controller                              |
| **Propósito** | Exponer API REST para gestión de grupos |
| **Ruta**      | `/api/group/`                           |

###### Tabla 101

_Tabla de métodos de GroupController en el Interface Layer de Asset & Resource Management_

| Nombre       | Ruta            | Acción                                 | Handle               |
|--------------|-----------------|----------------------------------------|----------------------|
| getGroup     | `/{id}`         | Obtener un grupo por ID                | `GetGroupQuery`      |
| getAllGroups | `/all/{userId}` | Obtener todos los grupos de un usuario | `GetAllGroupsQuery`  |
| updateGroup  | `/{id}`         | Actualizar datos de un grupo           | `UpdateGroupCommand` |
| createGroup  | `/create`       | Crear un nuevo grupo                   | `CreateGroupCommand` |
| deleteGroup  | `/{id}`         | Eliminar un grupo                      | `DeleteGroupCommand` |

#### 4.2.3.3. Asset & Resource Management Bounded Context Application Layer

La capa de aplicación del Bounded Context de Asset & Resource Management coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se ubican los Command Handlers, Query Handlers y Event Handlers, encargados de gestionar operaciones como el registro, actualización y seguimiento del estado de los activos físicos o virtuales dentro de Macetech, así como el procesamiento de eventos vinculados a su uso o mantenimiento. Esta capa garantiza que las interacciones se realicen de manera segura y transaccional, manteniendo la coherencia del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según sea necesario.

**GetPotQueryHandler**

###### Tabla 102

_Tabla de GetPotQueryHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                     |
|---------------|-----------------------------------------------------------|
| **Nombre**    | GetPotQueryHandler                                        |
| **Categoría** | Query Handler                                             |
| **Propósito** | Manejar la consulta `GetPotQuery` para obtener una maceta |

**GetAllPotsQueryHandler**

###### Tabla 103

_Tabla de GetAllPotsQueryHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                                   |
|---------------|-------------------------------------------------------------------------|
| **Nombre**    | GetAllPotsQueryHandler                                                  |
| **Categoría** | Query Handler                                                           |
| **Propósito** | Manejar la consulta `GetAllPotsQuery` para listar macetas de un usuario |

**GetAllPotsByGroupQueryHandler**

###### Tabla 104

_Tabla de GetAllPotsByGroupQueryHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                                      |
|---------------|----------------------------------------------------------------------------|
| **Nombre**    | GetAllPotsByGroupQueryHandler                                              |
| **Categoría** | Query Handler                                                              |
| **Propósito** | Manejar la consulta `GetAllPotsByGroupQuery` para listar macetas por grupo |

**UpdatePotCommandHandler**

###### Tabla 105

_Tabla de UpdatePotCommandHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                               |
|---------------|---------------------------------------------------------------------|
| **Nombre**    | UpdatePotCommandHandler                                             |
| **Categoría** | Command Handler                                                     |
| **Propósito** | Ejecutar la lógica de `UpdatePotCommand` para actualizar una maceta |

**LinkPotCommandHandler**

###### Tabla 106

_Tabla de LinkPotCommandHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                                       |
|---------------|-----------------------------------------------------------------------------|
| **Nombre**    | LinkPotCommandHandler                                                       |
| **Categoría** | Command Handler                                                             |
| **Propósito** | Ejecutar la lógica de `LinkPotCommand` para enlazar una maceta a un usuario |

**UnlinkPotCommandHandler**

###### Tabla 107

_Tabla de UnlinkPotCommandHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                                             |
|---------------|-----------------------------------------------------------------------------------|
| **Nombre**    | UnlinkPotCommandHandler                                                           |
| **Categoría** | Command Handler                                                                   |
| **Propósito** | Ejecutar la lógica de `UnlinkPotCommand` para desenlazar una maceta de un usuario |

**PotUpdatedEventHandler**

###### Tabla 108

_Tabla de PotUpdatedEventHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                               |
|---------------|-----------------------------------------------------|
| **Nombre**    | PotUpdatedEventHandler                              |
| **Categoría** | Event Handler                                       |
| **Propósito** | Procesar la lógica tras el evento `PotUpdatedEvent` |

**PotLinkedEventHandler**

###### Tabla 109

_Tabla de PotLinkedEventHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                              |
|---------------|----------------------------------------------------|
| **Nombre**    | PotLinkedEventHandler                              |
| **Categoría** | Event Handler                                      |
| **Propósito** | Procesar la lógica tras el evento `PotLinkedEvent` |

**PotUnlinkedEventHandler**

###### Tabla 110

_Tabla de PotUnlinkedEventHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                |
|---------------|------------------------------------------------------|
| **Nombre**    | PotUnlinkedEventHandler                              |
| **Categoría** | Event Handler                                        |
| **Propósito** | Procesar la lógica tras el evento `PotUnlinkedEvent` |

**PotAssignedPlantEventHandler**

###### Tabla 111

_Tabla de PotAssignedPlantEventHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                     |
|---------------|-----------------------------------------------------------|
| **Nombre**    | PotAssignedPlantEventHandler                              |
| **Categoría** | Event Handler                                             |
| **Propósito** | Procesar la lógica tras el evento `PotAssignedPlantEvent` |

**GetGroupQueryHandler**

###### Tabla 112

_Tabla de GetGroupQueryHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                     |
|---------------|-----------------------------------------------------------|
| **Nombre**    | GetGroupQueryHandler                                      |
| **Categoría** | Query Handler                                             |
| **Propósito** | Manejar la consulta `GetGroupQuery` para obtener un grupo |

**GetAllGroupsQueryHandler**

###### Tabla 113

_Tabla de GetAllGroupsQueryHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                                              |
|---------------|------------------------------------------------------------------------------------|
| **Nombre**    | GetAllGroupsQueryHandler                                                           |
| **Categoría** | Query Handler                                                                      |
| **Propósito** | Manejar la consulta `GetAllGroupsQuery` para listar todos los grupos de un usuario |

**UpdateGroupCommandHandler**

###### Tabla 114

_Tabla de UpdateGroupCommandHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                               |
|---------------|---------------------------------------------------------------------|
| **Nombre**    | UpdateGroupCommandHandler                                           |
| **Categoría** | Command Handler                                                     |
| **Propósito** | Ejecutar la lógica de `UpdateGroupCommand` para actualizar un grupo |

**CreateGroupCommandHandler**

###### Tabla 115

_Tabla de CreateGroupCommandHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                          |
|---------------|----------------------------------------------------------------|
| **Nombre**    | CreateGroupCommandHandler                                      |
| **Categoría** | Command Handler                                                |
| **Propósito** | Ejecutar la lógica de `CreateGroupCommand` para crear un grupo |

**DeleteGroupCommandHandler**

###### Tabla 116

_Tabla de DeleteGroupCommandHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                             |
|---------------|-------------------------------------------------------------------|
| **Nombre**    | DeleteGroupCommandHandler                                         |
| **Categoría** | Command Handler                                                   |
| **Propósito** | Ejecutar la lógica de `DeleteGroupCommand` para eliminar un grupo |

**GroupUpdatedEventHandler**

###### Tabla 117

_Tabla de GroupUpdatedEventHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                 |
|---------------|-------------------------------------------------------|
| **Nombre**    | GroupUpdatedEventHandler                              |
| **Categoría** | Event Handler                                         |
| **Propósito** | Procesar la lógica tras el evento `GroupUpdatedEvent` |

**GroupCreatedEventHandler**

###### Tabla 118

_Tabla de GroupCreatedEventHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                 |
|---------------|-------------------------------------------------------|
| **Nombre**    | GroupCreatedEventHandler                              |
| **Categoría** | Event Handler                                         |
| **Propósito** | Procesar la lógica tras el evento `GroupCreatedEvent` |

**GroupDeletedEventHandler**

###### Tabla 119

_Tabla de GroupDeletedEventHandler en el Application Layer de Asset & Resource Management_

| Propiedad     | Valor                                                 |
|---------------|-------------------------------------------------------|
| **Nombre**    | GroupDeletedEventHandler                              |
| **Categoría** | Event Handler                                         |
| **Propósito** | Procesar la lógica tras el evento `GroupDeletedEvent` |

#### 4.2.2.4. Asset & Resource Management Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Asset & Resource Management actúa como el vínculo entre la lógica de negocio y las tecnologías subyacentes que permiten la persistencia, comunicación e integración con sistemas externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, sensores físicos, servicios de monitoreo o catálogos de activos.

Esta capa concreta las abstracciones del dominio a través de implementaciones de repositorios y componentes técnicos especializados. Su diseño busca preservar el desacoplamiento respecto al núcleo del sistema, facilitando la evolución tecnológica sin afectar la consistencia de las reglas de negocio. Asimismo, garantiza eficiencia y confiabilidad en la gestión de inventarios, recursos físicos y sus respectivos estados operativos, en línea con los requerimientos estratégicos de la solución.

**PotRepository**

###### Tabla 120

_Tabla de PotRepository en el Infraestructure Layer de Asset & Resource Management_

| Propiedad     | Valor                                                            |
|---------------|------------------------------------------------------------------|
| **Nombre**    | PotRepository                                                    |
| **Categoría** | Repository Implementation                                        |
| **Propósito** | Implementar `IPotRepository` usando un mecanismo de persistencia |

**GroupRepository**

###### Tabla 121

_Tabla de GroupRepository en el Infraestructure Layer de Asset & Resource Management_

| Propiedad     | Valor                                                              |
|---------------|--------------------------------------------------------------------|
| **Nombre**    | GroupRepository                                                    |
| **Categoría** | Repository Implementation                                          |
| **Propósito** | Implementar `IGroupRepository` usando un mecanismo de persistencia |

#### 4.2.3.5. Asset & Resource Management Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Asset & Resource Management. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales relacionados con la gestión de activos y recursos dentro de la plataforma Macetech.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y eficiencia del sistema.

###### Figura 90
*Participación del Bounded Context de Asset & Resource Management con la aplicación móvil mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-MobileComponent.png"></image>

###### Figura 91
*Participación del Bounded Context de Asset & Resource Management con la aplicación web mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-WebComponent.png"></image>

###### Figura 92
*Participación del Bounded Context de Asset & Resource Management con la Cloud API mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-APIComponent.png"></image>

#### 4.2.3.6. Asset & Resource Management Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Asset & Resource Management, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 4.2.3.6.1. Asset & Resource Management Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Asset & Resource Management. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica del dominio, centrada en la gestión de activos físicos y recursos tecnológicos dentro del ecosistema Macetech.

El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y propósito en el modelo. Asimismo, se incluyen las relaciones entre elementos del dominio, cualificadas mediante nombres representativos, dirección cuando aplica y multiplicidad adecuada para reflejar con precisión las asociaciones entre entidades.

Esta vista detallada del diseño táctico facilita una comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación técnica, y asegurando la coherencia estructural en la gestión y trazabilidad de recursos en la plataforma.

###### Figura 93
*Diagrama de clases de la capa de dominio del Bounded Context de Asset & Resource Management*

<image src="../assets/img/capitulo-4/bounded-context-pot-management/class-diagram-pot-management.png"></image>

##### 4.2.3.6.2. Asset & Resource Management Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Asset & Resource Management. Esta representación permite visualizar de forma estructurada y precisa las entidades persistentes que forman parte de la gestión de activos físicos y recursos dentro de Macetech, así como sus atributos, claves primarias, claves foráneas y relaciones asociadas.

El diagrama incluye detalles fundamentales como los tipos de datos, las restricciones y la cardinalidad de las asociaciones entre tablas, lo que permite entender cómo se organiza la información a nivel de almacenamiento. Asimismo, se especifican las relaciones entre los distintos elementos, con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, reflejando de forma fidedigna la estructura lógica del modelo persistente.

Esta visualización detallada contribuye significativamente a la comprensión compartida del diseño de datos, sirviendo como puente entre el modelo de dominio y la implementación técnica de la base de datos, y asegurando que la arquitectura sea coherente, mantenible y alineada con los requerimientos del sistema.

###### Figura 94
*Diagrama de base de datos del Bounded Context de Asset & Resource Management*

<image src="../assets/img/capitulo-4/bounded-context-pot-management/database-diagram-pot-management.png"></image>

### 4.2.4. Bounded Context: Subscriptions & Payments

#### 4.2.4.1. Domain Layer.

## Subscription

| Propiedad     | Valor                                              |
|---------------|----------------------------------------------------|
| **Nombre**    | Subscription                                       |
| **Categoría** | Aggregate Root                                     |
| **Propósito** | Representar una suscripción activa para un usuario |

### Atributos

| Nombre    | Tipo de dato | Visibilidad | Descripción                                  |
|-----------|--------------|-------------|----------------------------------------------|
| userId    | `Long`       | private     | Identificador único del usuario              |
| planId    | `Long`       | private     | Identificador del plan de suscripción        |
| status    | `String`     | private     | Estado de la suscripción (activa, cancelada) |
| startDate | `DateTime`   | private     | Fecha de inicio de la suscripción            |
| endDate   | `DateTime`   | private     | Fecha de expiración de la suscripción        |
| createdAt | `DateTime`   | private     | Fecha de creación de la suscripción          |
| updatedAt | `DateTime`   | private     | Fecha de última actualización                |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                                 |
|--------------|-----------------|-------------|---------------------------------------------|
| activate     | `void`          | public      | Activa la suscripción                       |
| cancel       | `void`          | public      | Cancela la suscripción                      |
| updateStatus | `void`          | public      | Actualiza el estado de la suscripción       |
| markUpdated  | `void`          | private     | Actualiza internamente el campo `updatedAt` |

## SubscriptionPlan

| Propiedad     | Valor                                                         |
|---------------|---------------------------------------------------------------|
| **Nombre**    | SubscriptionPlan                                              |
| **Categoría** | Value Object                                                  |
| **Propósito** | Representar los detalles de un plan de suscripción disponible |

### Atributos

| Nombre    | Tipo de dato   | Visibilidad | Descripción                              |
|-----------|----------------|-------------|------------------------------------------|
| name      | `String`       | public      | Nombre del plan (p.ej., Básico, Premium) |
| price     | `Decimal`      | public      | Precio mensual del plan                  |
| duration  | `Int`          | public      | Duración del plan en meses               |
| features  | `List<String>` | public      | Características que ofrece el plan       |
| createdAt | `DateTime`     | private     | Fecha de creación del plan               |

## PaymentTransaction

| Propiedad     | Valor                                                                  |
|---------------|------------------------------------------------------------------------|
| **Nombre**    | PaymentTransaction                                                     |
| **Categoría** | Entity                                                                 |
| **Propósito** | Representar los pagos realizados por un usuario para sus suscripciones |

### Atributos

| Nombre         | Tipo de dato | Visibilidad | Descripción                                    |
|----------------|--------------|-------------|------------------------------------------------|
| transactionId  | `String`     | private     | Identificador único de la transacción          |
| subscriptionId | `Long`       | private     | Identificador de la suscripción                |
| amount         | `Decimal`    | private     | Monto de la transacción                        |
| status         | `String`     | private     | Estado de la transacción (completada, fallida) |
| createdAt      | `DateTime`   | private     | Fecha de la transacción                        |

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                 |
|----------------|-----------------|-------------|---------------------------------------------|
| processPayment | `void`          | public      | Procesa el pago para una suscripción        |
| updateStatus   | `void`          | public      | Actualiza el estado de la transacción       |
| markUpdated    | `void`          | private     | Actualiza internamente el campo `updatedAt` |

## ISubscriptionRepository

| Propiedad     | Valor                                          |
|---------------|------------------------------------------------|
| **Nombre**    | ISubscriptionRepository                        |
| **Categoría** | Repository                                     |
| **Propósito** | Persistir y recuperar entidades `Subscription` |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                                  |
|--------------|-----------------|-------------|----------------------------------------------|
| findByUserId | `Subscription?` | public      | Recupera la suscripción activa de un usuario |
| create       | `Unit`          | public      | Crea una nueva suscripción                   |
| update       | `Unit`          | public      | Actualiza una suscripción existente          |
| delete       | `Unit`          | public      | Elimina una suscripción por `userId`         |

## IPaymentTransactionRepository

| Propiedad     | Valor                                       |
|---------------|---------------------------------------------|
| **Nombre**    | IPaymentTransactionRepository               |
| **Categoría** | Repository                                  |
| **Propósito** | Persistir y recuperar transacciones de pago |

### Métodos

| Nombre   | Tipo de retorno       | Visibilidad | Descripción                                  |
|----------|-----------------------|-------------|----------------------------------------------|
| create   | `Unit`                | public      | Crea una nueva transacción de pago           |
| findById | `PaymentTransaction?` | public      | Recupera una transacción por `transactionId` |
| update   | `Unit`                | public      | Actualiza una transacción existente          |
| delete   | `Unit`                | public      | Elimina una transacción                      |

---

#### 4.2.4.2. Interface Layer.

## SubscriptionController

| Propiedad     | Valor                                                              |
|---------------|--------------------------------------------------------------------|
| **Nombre**    | SubscriptionController                                             |
| **Categoría** | Controller                                                         |
| **Propósito** | Exponer los servicios REST para gestionar suscripciones de usuario |
| **Ruta**      | `/api/subscriptions/`                                              |

### Métodos

| Nombre             | Ruta             | Acción                               | Handle                      |
|--------------------|------------------|--------------------------------------|-----------------------------|
| getSubscription    | `/{userId:long}` | Obtener la suscripción de un usuario | `GetSubscriptionQuery`      |
| createSubscription | `/create`        | Crear nueva suscripción              | `CreateSubscriptionCommand` |
| updateSubscription | `/update`        | Actualizar suscripción               | `UpdateSubscriptionCommand` |
| cancelSubscription | `/cancel`        | Cancelar suscripción                 | `CancelSubscriptionCommand` |

## PaymentTransactionController

| Propiedad     | Valor                                                           |
|---------------|-----------------------------------------------------------------|
| **Nombre**    | PaymentTransactionController                                    |
| **Categoría** | Controller                                                      |
| **Propósito** | Exponer los servicios REST para gestionar transacciones de pago |
| **Ruta**      | `/api/payment-transactions/`                                    |

### Métodos

| Nombre            | Ruta                    | Acción                                        | Handle                            |
|-------------------|-------------------------|-----------------------------------------------|-----------------------------------|
| getPayment        | `/{transactionId:long}` | Obtener transacción por ID                    | `GetPaymentTransactionQuery`      |
| createPayment     | `/create`               | Crear una nueva transacción                   | `CreatePaymentTransactionCommand` |
| updatePayment     | `/update`               | Actualizar estado de la transacción           | `UpdatePaymentTransactionCommand` |
| getPaymentsByUser | `/user/{userId:long}`   | Obtener todas las transacciones de un usuario | `GetPaymentsByUserQuery`          |

---

#### 4.2.4.3. Application Layer.

## GetSubscriptionQueryHandler

| Propiedad     | Valor                                                         |
|---------------|---------------------------------------------------------------|
| **Nombre**    | GetSubscriptionQueryHandler                                   |
| **Categoría** | Query Handler                                                 |
| **Propósito** | Manejar la consulta para obtener una suscripción por `userId` |

## CreateSubscriptionCommandHandler

| Propiedad     | Valor                                        |
|---------------|----------------------------------------------|
| **Nombre**    | CreateSubscriptionCommandHandler             |
| **Categoría** | Command Handler                              |
| **Propósito** | Manejar la creación de una nueva suscripción |

## UpdateSubscriptionCommandHandler

| Propiedad     | Valor                                                 |
|---------------|-------------------------------------------------------|
| **Nombre**    | UpdateSubscriptionCommandHandler                      |
| **Categoría** | Command Handler                                       |
| **Propósito** | Manejar la actualización de una suscripción existente |

## CancelSubscriptionCommandHandler

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | CancelSubscriptionCommandHandler          |
| **Categoría** | Command Handler                           |
| **Propósito** | Manejar la cancelación de una suscripción |

## GetPaymentTransactionQueryHandler

| Propiedad     | Valor                                                    |
|---------------|----------------------------------------------------------|
| **Nombre**    | GetPaymentTransactionQueryHandler                        |
| **Categoría** | Query Handler                                            |
| **Propósito** | Manejar la consulta para obtener una transacción de pago |

## GetPaymentsByUserQueryHandler

| Propiedad     | Valor                                                            |
|---------------|------------------------------------------------------------------|
| **Nombre**    | GetPaymentsByUserQueryHandler                                    |
| **Categoría** | Query Handler                                                    |
| **Propósito** | Manejar la consulta para obtener las transacciones de un usuario |

---

#### 4.2.4.4. Infrastructure Layer.

## SubscriptionRepository

| Propiedad     | Valor                                                                     |
|---------------|---------------------------------------------------------------------------|
| **Nombre**    | SubscriptionRepository                                                    |
| **Categoría** | Repository Implementation                                                 |
| **Propósito** | Implementar `ISubscriptionRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                           |
|--------------|-----------------|-------------|---------------------------------------|
| findByUserId | `Subscription?` | public      | Recupera la suscripción de un usuario |
| create       | `Unit`          | public      | Persistir una nueva suscripción       |
| update       | `Unit`          | public      | Actualiza una suscripción existente   |
| delete       | `Unit`          | public      | Elimina la suscripción por `userId`   |

## PaymentTransactionRepository

| Propiedad     | Valor                                                                           |
|---------------|---------------------------------------------------------------------------------|
| **Nombre**    | PaymentTransactionRepository                                                    |
| **Categoría** | Repository Implementation                                                       |
| **Propósito** | Implementar `IPaymentTransactionRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre   | Tipo de retorno       | Visibilidad | Descripción                                  |
|----------|-----------------------|-------------|----------------------------------------------|
| create   | `Unit`                | public      | Persistir una nueva transacción de pago      |
| findById | `PaymentTransaction?` | public      | Recupera una transacción por `transactionId` |
| update   | `Unit`                | public      | Actualiza una transacción existente          |
| delete   | `Unit`                | public      | Elimina una transacción                      |

---

#### 4.2.4.5. Subscriptions & Payments Bounded Context Software Architecture Component Level Diagrams.

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-subscription--component.png"></image>

#### 4.2.4.6. Subscriptions & Payments Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.4.6.1. Subscriptions & Payments Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-subscriptions-and-payments/Subscription&PaymentsClassDiagram.png"></image>

##### 4.2.4.6.2. Bounded Context Database Design Diagram.
<image src="../assets/img/capitulo-4/bounded-context-subscriptions-and-payments/Subscriptions&PaymentsDbDiagram.png"></image>

### 4.2.5. Bounded Context: Service Design and Planning

#### 4.2.5.1. Domain Layer.

## Plant

| Propiedad     | Valor                                                      |
|---------------|------------------------------------------------------------|
| **Nombre**    | Plant                                                      |
| **Categoría** | Aggregate Root                                             |
| **Propósito** | Representar la relación planta–maceta con marcas de tiempo |

### Atributos

| Nombre            | Tipo de dato        | Visibilidad | Descripción                         |
|-------------------|---------------------|-------------|-------------------------------------|
| id                | `Long`              | private     | Identificador único de la planta    |
| potId             | `Long`              | private     | Identificador de la maceta asociada |
| bestPlantSettings | `BestPlantSettings` | private     | Entorno óptimo para la planta       |
| plantInformation  | `PlantInformation`  | private     | Información de la planta            |
| createdAt         | `DateTime`          | private     | Fecha de creación de la entidad     |
| updatedAt         | `DateTime`          | private     | Fecha de última actualización       |

### Métodos

| Nombre      | Tipo de retorno | Visibilidad | Descripción                                    |
|-------------|-----------------|-------------|------------------------------------------------|
| changePot   | `void`          | public      | Reasigna a otra maceta y actualiza `updatedAt` |
| markUpdated | `void`          | private     | Actualiza internamente el campo `updatedAt`    |

## BestPlantSettings

| Propiedad     | Valor                                                     |
|---------------|-----------------------------------------------------------|
| **Nombre**    | BestPlantSettings                                         |
| **Categoría** | Value Object                                              |
| **Propósito** | Representar la información de entorno óptimo de la planta |

### Atributos

| Nombre                 | Tipo de dato | Visibilidad | Descripción                                    |
|------------------------|--------------|-------------|------------------------------------------------|
| humidity               | `Float`      | public      | Nivel de humedad óptimo                        |
| temperature            | `Float`      | public      | Temperatura óptima                             |
| waterIntervalInMinutes | `Int`        | public      | Recomendación de riego por intervalo de tiempo |

## PlantInformation

| Propiedad     | Valor                                   |
|---------------|-----------------------------------------|
| **Nombre**    | PlantInformation                        |
| **Categoría** | Value Object                            |
| **Propósito** | Representar la información de la planta |

### Atributos

| Nombre      | Tipo de dato | Visibilidad | Descripción                     |
|-------------|--------------|-------------|---------------------------------|
| name        | `String`     | public      | Nombre de la planta             |
| description | `String`     | public      | Descripción de la planta        |
| imageUrl    | `String`     | public      | Imagen referencial de la planta |
| family      | `String`     | public      | Familia de la planta            |
| genus       | `String`     | public      | Género de la planta             |
| species     | `String`     | public      | Especie de la planta            |

## PlantFactory

| Propiedad     | Valor                                  |
|---------------|----------------------------------------|
| **Nombre**    | PlantFactory                           |
| **Categoría** | Factory                                |
| **Propósito** | Construir nuevas instancias de `Plant` |

### Métodos

| Nombre | Tipo de retorno | Visibilidad | Descripción                                                        |
|--------|-----------------|-------------|--------------------------------------------------------------------|
| create | `Plant`         | public      | Crea un `Plant` dado `potId`, inicializa `createdAt` y `updatedAt` |

## IPlantRepository

| Propiedad     | Valor                                   |
|---------------|-----------------------------------------|
| **Nombre**    | IPlantRepository                        |
| **Categoría** | Repository                              |
| **Propósito** | Persistir y recuperar entidades `Plant` |

### Métodos

| Nombre   | Tipo de retorno | Visibilidad | Descripción                    |
|----------|-----------------|-------------|--------------------------------|
| findById | `Plant?`        | public      | Busca una planta por su ID     |
| create   | `Unit`          | public      | Persiste una nueva planta      |
| update   | `Unit`          | public      | Actualiza una planta existente |
| delete   | `Unit`          | public      | Elimina una planta por su ID   |

## IPlantRecommendationService

| Propiedad     | Valor                                               |
|---------------|-----------------------------------------------------|
| **Nombre**    | IPlantRecommendationService                         |
| **Categoría** | Domain Service                                      |
| **Propósito** | Proveer la mejor configuración para una planta dada |

### Métodos

| Nombre               | Tipo de retorno | Visibilidad | Descripción                            |
|----------------------|-----------------|-------------|----------------------------------------|
| getBestPlantSettings | `String?`       | public      | Retorna ajustes óptimos para la planta |

## PlantRecommendationService

| Propiedad     | Valor                                                   |
|---------------|---------------------------------------------------------|
| **Nombre**    | PlantRecommendationService                              |
| **Categoría** | Domain Service Implementation                           |
| **Propósito** | Implementar la lógica de recomendación de configuración |

#### 4.2.5.2. Interface Layer.

## PlantController

| Propiedad     | Valor                                          |
|---------------|------------------------------------------------|
| **Nombre**    | PlantController                                |
| **Categoría** | Controller                                     |
| **Propósito** | Exponer endpoints REST para gestión de plantas |
| **Ruta**      | `/api/plant/`                                  |

## Métodos

| Nombre      | Ruta            | Acción                         | Handle               |
|-------------|-----------------|--------------------------------|----------------------|
| getPlant    | `/{id:long}`    | Obtener detalles de una planta | `GetPlantQuery`      |
| createPlant | `/create`       | Crear nueva planta             | `CreatePlantCommand` |
| updatePlant | `/update`       | Actualizar planta existente    | `UpdatePlantCommand` |
| deletePlant | `/delete-plant` | Eliminar planta por su ID      | `DeletePlantCommand` |

#### 4.2.5.3. Application Layer.

## GetPlantQueryHandler

| Propiedad     | Valor                                      |
|---------------|--------------------------------------------|
| **Nombre**    | GetPlantQueryHandler                       |
| **Categoría** | Query Handler                              |
| **Propósito** | Manejar la consulta de obtención de planta |

## CreatePlantCommandHandler

| Propiedad     | Valor                                 |
|---------------|---------------------------------------|
| **Nombre**    | CreatePlantCommandHandler             |
| **Categoría** | Command Handler                       |
| **Propósito** | Ejecutar lógica de creación de planta |

## UpdatePlantCommandHandler

| Propiedad     | Valor                                      |
|---------------|--------------------------------------------|
| **Nombre**    | UpdatePlantCommandHandler                  |
| **Categoría** | Command Handler                            |
| **Propósito** | Ejecutar lógica de actualización de planta |

## DeletePlantCommandHandler

| Propiedad     | Valor                                    |
|---------------|------------------------------------------|
| **Nombre**    | DeletePlantCommandHandler                |
| **Categoría** | Command Handler                          |
| **Propósito** | Ejecutar lógica de eliminación de planta |

## PlantCreatedEventHandler

| Propiedad     | Valor                                 |
|---------------|---------------------------------------|
| **Nombre**    | PlantCreatedEventHandler              |
| **Categoría** | Event Handler                         |
| **Propósito** | Reaccionar al evento de planta creada |

## PlantUpdatedEventHandler

| Propiedad     | Valor                                      |
|---------------|--------------------------------------------|
| **Nombre**    | PlantUpdatedEventHandler                   |
| **Categoría** | Event Handler                              |
| **Propósito** | Reaccionar al evento de planta actualizada |

## PlantDeletedEventHandler

| Propiedad     | Valor                                    |
|---------------|------------------------------------------|
| **Nombre**    | PlantDeletedEventHandler                 |
| **Categoría** | Event Handler                            |
| **Propósito** | Reaccionar al evento de planta eliminada |

## IPlantInfoProvider

| Propiedad     | Valor                                                        |
|---------------|--------------------------------------------------------------|
| **Nombre**    | IPlantInfoProvider                                           |
| **Categoría** | Interface (Application Service)                              |
| **Propósito** | Obtener especificaciones de planta desde un servicio externo |

#### 4.2.5.4. Infrastructure Layer.

## PlantRepository

| Propiedad     | Valor                                  |
|---------------|----------------------------------------|
| **Nombre**    | PlantRepository                        |
| **Categoría** | Repository Implementation              |
| **Propósito** | Implementar `IPlantRepository` con ORM |

### Métodos

| Nombre        | Tipo de retorno | Visibilidad | Descripción                 |
|---------------|-----------------|-------------|-----------------------------|
| findById      | `Plant?`        | public      | Busca planta por su ID      |
| findByPotId   | `List<Plant>`   | public      | Lista plantas de una maceta |
| findByUserUid | `List<Plant>`   | public      | Lista plantas de un usuario |
| create        | `Unit`          | public      | Persiste nueva planta       |
| update        | `Unit`          | public      | Actualiza planta existente  |
| delete        | `Unit`          | public      | Elimina planta por ID       |

## PlantInfoProvider

| Propiedad     | Valor                                                         |
|---------------|---------------------------------------------------------------|
| **Nombre**    | PlantInfoProvider                                             |
| **Categoría** | External Service Implementation                               |
| **Propósito** | Implementar `IPlantInfoProvider` para obtener specs de planta |

#### 4.2.5.5. Plant Management Bounded Context Software Architecture Component Level Diagrams.
 
<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-plant-component.png"></image>

#### 4.2.5.6. Plant Management Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.5.6.1. Plant Management Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-plant-management/class-diagram-plant-management.png"></image>

##### 4.2.5.6.2. Bounded Context Database Design Diagram.
<image src="../assets/img/capitulo-4/bounded-context-plant-management/database-diagram-plant-management.png"></image>

### 4.2.6. Bounded Context: Service Monitoring & Operations

#### 4.2.6.1. Domain Layer.

## WateringSchedule

| Propiedad     | Valor                                                            |
|---------------|------------------------------------------------------------------|
| **Nombre**    | WateringSchedule                                                 |
| **Categoría** | Aggregate Root                                                   |
| **Propósito** | Representar una programación de riego para una maceta específica |

### Atributos

| Nombre    | Tipo de dato | Visibilidad | Descripción                                 |
|-----------|--------------|-------------|---------------------------------------------|
| potId     | `long`       | private     | Identificador de la maceta                  |
| startTime | `DateTime`   | private     | Hora de inicio del riego                    |
| frequency | `string`     | private     | Frecuencia (diaria, semanal, personalizada) |
| duration  | `int`        | private     | Duración en minutos                         |
| isActive  | `bool`       | private     | Si la programación está activa o suspendida |
| createdAt | `DateTime`   | private     | Fecha de creación                           |
| updatedAt | `DateTime`   | private     | Última fecha de actualización               |

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                 |
|----------------|-----------------|-------------|---------------------------------------------|
| updateSchedule | `void`          | public      | Modifica horario, frecuencia o duración     |
| activate       | `void`          | public      | Activa la programación                      |
| deactivate     | `void`          | public      | Suspende la programación                    |
| markUpdated    | `void`          | private     | Actualiza internamente el campo `updatedAt` |

## WateringLog

| Propiedad     | Valor                                          |
|---------------|------------------------------------------------|
| **Nombre**    | WateringLog                                    |
| **Categoría** | Entity                                         |
| **Propósito** | Registrar una ejecución de riego en una maceta |

### Atributos

| Nombre    | Tipo de dato | Visibilidad | Descripción                             |
|-----------|--------------|-------------|-----------------------------------------|
| id        | `Long`       | private     | Identificador del log                   |
| potId     | `Long`       | private     | Identificador de la maceta              |
| timestamp | `DateTime`   | private     | Momento de ejecución                    |
| status    | `String`     | private     | Estado del riego (exitoso, error, etc.) |

## IWateringScheduleRepository

| Propiedad     | Valor                                        |
|---------------|----------------------------------------------|
| **Nombre**    | IWateringScheduleRepository                  |
| **Categoría** | Repository                                   |
| **Propósito** | Gestionar persistencia de `WateringSchedule` |

### Métodos

| Nombre      | Tipo de retorno     | Descripción                           |
|-------------|---------------------|---------------------------------------|
| findByPotId | `WateringSchedule?` | Obtener programación de riego         |
| create      | `Unit`              | Guardar nueva programación            |
| update      | `Unit`              | Actualizar una programación existente |
| delete      | `Unit`              | Eliminar programación por `potId`     |

## IWateringLogRepository

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | IWateringLogRepository                    |
| **Categoría** | Repository                                |
| **Propósito** | Gestionar registros de ejecución de riego |

### Métodos

| Nombre      | Tipo de retorno     | Descripción                       |
|-------------|---------------------|-----------------------------------|
| create      | `Unit`              | Almacenar un nuevo `WateringLog`  |
| findByPotId | `List<WateringLog>` | Consultar registros de una maceta |

---

#### 4.2.6.2. Interface Layer.

## WateringScheduleController

| Propiedad     | Valor                                                              |
|---------------|--------------------------------------------------------------------|
| **Nombre**    | WateringScheduleController                                         |
| **Categoría** | Controller                                                         |
| **Propósito** | Exponer los servicios REST para gestionar la programación de riego |
| **Ruta**      | `/api/watering-schedules/`                                         |

### Métodos

| Nombre             | Ruta          | Acción                             | Handle                              |
|--------------------|---------------|------------------------------------|-------------------------------------|
| getSchedule        | `/{id:long}`  | Obtener programación de riego      | `GetWateringScheduleQuery`          |
| createSchedule     | `/create`     | Crear nueva programación de riego  | `CreateWateringScheduleCommand`     |
| updateSchedule     | `/update`     | Actualizar programación existente  | `UpdateWateringScheduleCommand`     |
| deactivateSchedule | `/deactivate` | Suspender la programación de riego | `DeactivateWateringScheduleCommand` |
| activateSchedule   | `/activate`   | Activar la programación de riego   | `ActivateWateringScheduleCommand`   |

## WateringLogController

| Propiedad     | Valor                                                       |
|---------------|-------------------------------------------------------------|
| **Nombre**    | WateringLogController                                       |
| **Categoría** | Controller                                                  |
| **Propósito** | Exponer los servicios REST para consultar los logs de riego |
| **Ruta**      | `/api/watering-logs/`                                       |

### Métodos

| Nombre       | Ruta                | Acción                              | Handle                      |
|--------------|---------------------|-------------------------------------|-----------------------------|
| getLog       | `/{id:long}`        | Obtener log de riego por ID         | `GetWateringLogQuery`       |
| getLogsByPot | `/pot/{potId:long}` | Obtener logs de riego de una maceta | `GetWateringLogsByPotQuery` |

---

#### 4.2.6.3. Application Layer.

## GetWateringScheduleQueryHandler

| Propiedad     | Valor                                                             |
|---------------|-------------------------------------------------------------------|
| **Nombre**    | GetWateringScheduleQueryHandler                                   |
| **Categoría** | Query Handler                                                     |
| **Propósito** | Manejar la consulta para obtener una programación de riego por ID |

## CreateWateringScheduleCommandHandler

| Propiedad     | Valor                                                  |
|---------------|--------------------------------------------------------|
| **Nombre**    | CreateWateringScheduleCommandHandler                   |
| **Categoría** | Command Handler                                        |
| **Propósito** | Manejar la creación de una nueva programación de riego |

## UpdateWateringScheduleCommandHandler

| Propiedad     | Valor                                                           |
|---------------|-----------------------------------------------------------------|
| **Nombre**    | UpdateWateringScheduleCommandHandler                            |
| **Categoría** | Command Handler                                                 |
| **Propósito** | Manejar la actualización de una programación de riego existente |

## DeactivateWateringScheduleCommandHandler

| Propiedad     | Valor                                                 |
|---------------|-------------------------------------------------------|
| **Nombre**    | DeactivateWateringScheduleCommandHandler              |
| **Categoría** | Command Handler                                       |
| **Propósito** | Manejar la desactivación de una programación de riego |

## ActivateWateringScheduleCommandHandler

| Propiedad     | Valor                                              |
|---------------|----------------------------------------------------|
| **Nombre**    | ActivateWateringScheduleCommandHandler             |
| **Categoría** | Command Handler                                    |
| **Propósito** | Manejar la activación de una programación de riego |

## GetWateringLogQueryHandler

| Propiedad     | Valor                                       |
|---------------|---------------------------------------------|
| **Nombre**    | GetWateringLogQueryHandler                  |
| **Categoría** | Query Handler                               |
| **Propósito** | Manejar la consulta de logs de riego por ID |

## GetWateringLogsByPotQueryHandler

| Propiedad     | Valor                                                   |
|---------------|---------------------------------------------------------|
| **Nombre**    | GetWateringLogsByPotQueryHandler                        |
| **Categoría** | Query Handler                                           |
| **Propósito** | Manejar la consulta de logs de riego por potId (maceta) |

---

#### 4.2.6.4. Infrastructure Layer.

## WateringScheduleRepository

| Propiedad     | Valor                                                                         |
|---------------|-------------------------------------------------------------------------------|
| **Nombre**    | WateringScheduleRepository                                                    |
| **Categoría** | Repository Implementation                                                     |
| **Propósito** | Implementar `IWateringScheduleRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre      | Tipo de retorno     | Visibilidad | Descripción                                    |
|-------------|---------------------|-------------|------------------------------------------------|
| findByPotId | `WateringSchedule?` | public      | Buscar programación de riego por `potId`       |
| create      | `Unit`              | public      | Persistir una nueva programación de riego      |
| update      | `Unit`              | public      | Actualizar una programación de riego existente |
| delete      | `Unit`              | public      | Eliminar programación de riego por `potId`     |

## WateringLogRepository

| Propiedad     | Valor                                                                    |
|---------------|--------------------------------------------------------------------------|
| **Nombre**    | WateringLogRepository                                                    |
| **Categoría** | Repository Implementation                                                |
| **Propósito** | Implementar `IWateringLogRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre      | Tipo de retorno     | Visibilidad | Descripción                         |
|-------------|---------------------|-------------|-------------------------------------|
| create      | `Unit`              | public      | Persistir un nuevo log de riego     |
| findByPotId | `List<WateringLog>` | public      | Recuperar logs de riego por `potId` |

---

#### 4.2.6.5. Watering Management Bounded Context Software Architecture Component Level Diagrams.

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-watering-component.png"></image>

#### 4.2.6.6. Watering Management Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.6.6.1. Watering Management Bounded Context Domain Layer Class Diagrams.
<image src="../assets/img/capitulo-4/bounded-context-watering-management/WateringScheduleClassDiagram.png"></image>

##### 4.2.6.6.2. Bounded Context Database Design Diagram.
<image src="../assets/img/capitulo-4/bounded-context-watering-management/WateringManagementDbDiagram.png"></image>

### 4.2.7. Bounded Context: Data Analytics

#### 4.2.7.1. Domain Layer.

## Recommendation

| Propiedad     | Valor                                                             |
|---------------|-------------------------------------------------------------------|
| **Nombre**    | Recommendation                                                    |
| **Categoría** | Aggregate Root                                                    |
| **Propósito** | Generar recomendaciones personalizadas para el cuidado de plantas |

### Atributos

| Nombre             | Tipo de dato | Visibilidad | Descripción                                       |
|--------------------|--------------|-------------|---------------------------------------------------|
| plantId            | `Long`       | private     | Identificador de la planta                        |
| userId             | `Long`       | private     | Identificador del usuario                         |
| recommendationType | `String`     | private     | Tipo de recomendación (riego, luz, fertilización) |
| value              | `String`     | private     | Valor o mensaje de la recomendación               |
| createdAt          | `DateTime`   | private     | Fecha de creación                                 |
| updatedAt          | `DateTime`   | private     | Fecha de última actualización                     |

### Métodos

| Nombre                 | Tipo de retorno | Visibilidad | Descripción                                            |
|------------------------|-----------------|-------------|--------------------------------------------------------|
| generateRecommendation | `void`          | public      | Genera una recomendación personalizada para el usuario |
| markUpdated            | `void`          | private     | Actualiza internamente el campo `updatedAt`            |

## PlantRecommendation

| Propiedad     | Valor                                                       |
|---------------|-------------------------------------------------------------|
| **Nombre**    | PlantRecommendation                                         |
| **Categoría** | Value Object                                                |
| **Propósito** | Contener los parámetros de la recomendación para una planta |

### Atributos

| Nombre      | Tipo de dato | Visibilidad | Descripción                  |
|-------------|--------------|-------------|------------------------------|
| humidity    | `String`     | public      | Recomendación de humedad     |
| light       | `String`     | public      | Recomendación de luz         |
| water       | `String`     | public      | Recomendación de riego       |
| temperature | `String`     | public      | Recomendación de temperatura |

## DataReport

| Propiedad     | Valor                                                  |
|---------------|--------------------------------------------------------|
| **Nombre**    | DataReport                                             |
| **Categoría** | Aggregate Root                                         |
| **Propósito** | Generar y almacenar reportes de datos para su análisis |

### Atributos

| Nombre      | Tipo de dato | Visibilidad | Descripción                                   |
|-------------|--------------|-------------|-----------------------------------------------|
| reportId    | `Long`       | private     | Identificador único del reporte               |
| userId      | `Long`       | private     | Identificador del usuario asociado al reporte |
| data        | `String`     | private     | Datos relevantes del reporte                  |
| reportType  | `String`     | private     | Tipo de reporte (mensual, anual, etc.)        |
| generatedAt | `DateTime`   | private     | Fecha de generación del reporte               |
| createdAt   | `DateTime`   | private     | Fecha de creación                             |
| updatedAt   | `DateTime`   | private     | Fecha de última actualización                 |

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                 |
|----------------|-----------------|-------------|---------------------------------------------|
| generateReport | `void`          | public      | Genera un nuevo reporte                     |
| markUpdated    | `void`          | private     | Actualiza internamente el campo `updatedAt` |

## DataSource

| Propiedad     | Valor                                        |
|---------------|----------------------------------------------|
| **Nombre**    | DataSource                                   |
| **Categoría** | Value Object                                 |
| **Propósito** | Representar la fuente de datos de un reporte |

### Atributos

| Nombre          | Tipo de dato | Visibilidad | Descripción                                     |
|-----------------|--------------|-------------|-------------------------------------------------|
| sourceId        | `Long`       | private     | Identificador de la fuente de datos             |
| dataType        | `String`     | private     | Tipo de los datos (e.g., sensor, usuario, etc.) |
| dataDescription | `String`     | private     | Descripción de los datos                        |
| createdAt       | `DateTime`   | private     | Fecha de creación                               |

---
#### 4.2.7.2. Interface Layer.

## RecommendationController

| Propiedad     | Valor                                                     |
|---------------|-----------------------------------------------------------|
| **Nombre**    | RecommendationController                                  |
| **Categoría** | Controller                                                |
| **Propósito** | Exponer los servicios REST para gestionar recomendaciones |
| **Ruta**      | `/api/recommendations/`                                   |

### Métodos

| Nombre               | Ruta                            | Acción                            | Handle                        |
|----------------------|---------------------------------|-----------------------------------|-------------------------------|
| getRecommendation    | `/{userId:long}/{plantId:long}` | Obtener recomendación para planta | `GetRecommendationQuery`      |
| createRecommendation | `/create`                       | Crear nueva recomendación         | `CreateRecommendationCommand` |
| updateRecommendation | `/update`                       | Actualizar recomendación          | `UpdateRecommendationCommand` |

## DataReportController

| Propiedad     | Valor                                                       |
|---------------|-------------------------------------------------------------|
| **Nombre**    | DataReportController                                        |
| **Categoría** | Controller                                                  |
| **Propósito** | Exponer los servicios REST para gestionar reportes de datos |
| **Ruta**      | `/api/data-reports/`                                        |

### Métodos

| Nombre           | Ruta                             | Acción                                      | Handle                    |
|------------------|----------------------------------|---------------------------------------------|---------------------------|
| getReport        | `/{userId:long}/{reportId:long}` | Obtener reporte por ID de usuario y reporte | `GetDataReportQuery`      |
| createReport     | `/create`                        | Crear nuevo reporte                         | `CreateDataReportCommand` |
| updateReport     | `/update`                        | Actualizar reporte existente                | `UpdateDataReportCommand` |
| getReportsByUser | `/user/{userId:long}`            | Obtener todos los reportes de un usuario    | `GetReportsByUserQuery`   |

---

#### 4.2.7.3. Application Layer.

## GetRecommendationQueryHandler

| Propiedad     | Valor                                                            |
|---------------|------------------------------------------------------------------|
| **Nombre**    | GetRecommendationQueryHandler                                    |
| **Categoría** | Query Handler                                                    |
| **Propósito** | Manejar la consulta para obtener una recomendación personalizada |

## CreateRecommendationCommandHandler

| Propiedad     | Valor                                          |
|---------------|------------------------------------------------|
| **Nombre**    | CreateRecommendationCommandHandler             |
| **Categoría** | Command Handler                                |
| **Propósito** | Manejar la creación de una nueva recomendación |

## UpdateRecommendationCommandHandler

| Propiedad     | Valor                                                   |
|---------------|---------------------------------------------------------|
| **Nombre**    | UpdateRecommendationCommandHandler                      |
| **Categoría** | Command Handler                                         |
| **Propósito** | Manejar la actualización de una recomendación existente |

## GetDataReportQueryHandler

| Propiedad     | Valor                                                |
|---------------|------------------------------------------------------|
| **Nombre**    | GetDataReportQueryHandler                            |
| **Categoría** | Query Handler                                        |
| **Propósito** | Manejar la consulta para obtener un reporte de datos |

## CreateDataReportCommandHandler

| Propiedad     | Valor                                            |
|---------------|--------------------------------------------------|
| **Nombre**    | CreateDataReportCommandHandler                   |
| **Categoría** | Command Handler                                  |
| **Propósito** | Manejar la creación de un nuevo reporte de datos |

## UpdateDataReportCommandHandler

| Propiedad     | Valor                                           |
|---------------|-------------------------------------------------|
| **Nombre**    | UpdateDataReportCommandHandler                  |
| **Categoría** | Command Handler                                 |
| **Propósito** | Manejar la actualización de un reporte de datos |

---

#### 4.2.7.4. Infrastructure Layer.

## RecommendationRepository

| Propiedad     | Valor                                                                       |
|---------------|-----------------------------------------------------------------------------|
| **Nombre**    | RecommendationRepository                                                    |
| **Categoría** | Repository Implementation                                                   |
| **Propósito** | Implementar `IRecommendationRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre       | Tipo de retorno   | Visibilidad | Descripción                            |
|--------------|-------------------|-------------|----------------------------------------|
| findByUserId | `Recommendation?` | public      | Obtener la recomendación por `userId`  |
| create       | `Unit`            | public      | Crear una nueva recomendación          |
| update       | `Unit`            | public      | Actualizar una recomendación existente |
| delete       | `Unit`            | public      | Eliminar la recomendación              |

## DataReportRepository

| Propiedad     | Valor                                                                   |
|---------------|-------------------------------------------------------------------------|
| **Nombre**    | DataReportRepository                                                    |
| **Categoría** | Repository Implementation                                               |
| **Propósito** | Implementar `IDataReportRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre       | Tipo de retorno | Visibilidad | Descripción                      |
|--------------|-----------------|-------------|----------------------------------|
| findByUserId | `DataReport?`   | public      | Recupera un reporte por `userId` |
| create       | `Unit`          | public      | Crear un nuevo reporte           |
| update       | `Unit`          | public      | Actualiza un reporte existente   |
| delete       | `Unit`          | public      | Elimina un reporte               |

## DataSourceRepository

| Propiedad     | Valor                                                                   |
|---------------|-------------------------------------------------------------------------|
| **Nombre**    | DataSourceRepository                                                    |
| **Categoría** | Repository Implementation                                               |
| **Propósito** | Implementar `IDataSourceRepository` usando un mecanismo de persistencia |

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                |
|----------------|-----------------|-------------|--------------------------------------------|
| findBySourceId | `DataSource?`   | public      | Recupera la fuente de datos por `sourceId` |
| create         | `Unit`          | public      | Crear una nueva fuente de datos            |
| update         | `Unit`          | public      | Actualiza una fuente de datos existente    |
| delete         | `Unit`          | public      | Elimina una fuente de datos                |

---
#### 4.2.7.5. Data Analytics Bounded Context Software Architecture Component Level Diagrams.

<image src="../assets/img/capitulo-4/c4-model/structurizr-102464-recommendation-component.png"></image>

#### 4.2.7.6. Data Analytics Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.7.6.1. Bounded Context Domain Layer Class Diagrams.

<image src="../assets/img/capitulo-4/bounded-context-caring-intelligence/CaringIntelligenceClassDiagram.png"></image>

##### 4.2.7.6.2. Bounded Context Database Design Diagram.
<image src="../assets/img/capitulo-4/bounded-context-caring-intelligence/CaringIntelligenceDbDiagram.png"></image>
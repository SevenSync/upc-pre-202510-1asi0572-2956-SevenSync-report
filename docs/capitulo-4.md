# Capítulo IV: Solution Software Design

## 4.1. Strategic-Level Domain-Driven Design.

Strategic Domain-Driven Design, o DDD estratégico es un enfoque arquitectónico que busca alinear la estructura del software con la lógica del negocio y la organización. Este enfoque es esencial para gestionar la complejidad en sistemas grandes y distribuidos, especialmente cuando múltiples equipos trabajan en diferentes partes del sistema.

Según Eric Evans, quien introdujo el concepto de DDD en su libro Domain-Driven Design: Tackling Complexity in the Heart of Software, el enfoque estratégico se centra en definir límites claros dentro del dominio, conocidos como Bounded Contexts, y en establecer un lenguaje común, o Lenguaje Ubicuo, que facilite la comunicación entre desarrolladores y expertos del dominio.

Vaughn Vernon, en su obra Implementing Domain-Driven Design, amplía esta perspectiva al dividir el dominio en dos espacios: el espacio del problema y el espacio de la solución. El primero se enfoca en entender los problemas del negocio, mientras que el segundo aborda cómo resolverlos mediante soluciones técnicas adecuadas.

Para abordar las decisiones estratégicas en el diseño de software utilizando Domain-Driven Design (DDD), el equipo ha implementado un proceso estructurado que combina técnicas colaborativas y herramientas visuales. Este enfoque facilita la identificación de límites naturales dentro del dominio del negocio, conocidos como Bounded Contexts, y promueve una comprensión compartida entre todos los participantes.

### 4.1.1. EventStorming.

En esta sección se documenta el proceso realizado mediante la técnica de EventStorming, con el propósito de obtener una comprensión compartida del dominio del problema y definir una primera aproximación al modelo del sistema. Esta técnica, introducida por Alberto Brandolini, permite identificar eventos clave del negocio de manera colaborativa entre expertos del dominio y el equipo técnico, y constituye una base sólida para aplicar Domain-Driven Design (DDD).

> “EventStorming is a workshop format for quickly exploring complex business domains. It is designed to bring together different stakeholders to collaboratively model business processes using domain events.” (Brandolini, 2013)

Como objetivos tuvimos: 
- Identificar eventos relevantes que ocurren dentro del dominio.

- Establecer relaciones causales y temporales entre eventos.

- Detectar procesos del negocio, comandos y actores implicados.

- Servir como insumo para definir Bounded Contexts posteriormente.

###### Desarrollo de la sesión

 <b>Fase 1: Recolección de Domain Events (Big Picture)</b>

En esta etapa inicial, cada participante propuso eventos profesionales del sistema utilizando notas adhesivas naranjas. Estos eventos representan hechos relevantes que ocurren en el negocio, expresados en pasado.

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-1-collect-domain-events.jpg"></image>

- Fase 2: Refinamiento de Domain Events

En una segunda ronda colaborativa, se depuraron los eventos recolectados: se eliminaron duplicados, se aclararon ambigüedades y se reorganizaron cronológicamente. También se discutió la terminología para asegurar coherencia y precisión semántica.

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-2-timeline-and-refine-domain-events.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-2-1-collect-domain-events.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-2-2-collect-domain-events.jpg.jpg"></image>

Fase 3: Rastrear las Causas: Durante esta fase, se analizaron los eventos para identificar sus causas. Se consideraron cuatro tipos principales de disparadores:
- Acciones de usuarios (comandos, actores, vistas),
- Sistemas externos,
- Procesos de negocio (por ejemplo, condiciones temporales),
- Otros eventos del dominio (reacciones automáticas).

Para esta sección, se necesitará identificar el color de los post-its de Miro para mantener el orden. Se usará esta convención:
 
 <image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-summary.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-alerts.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-data-ingestion.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-iam.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-notifications.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-notifications.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-plant-management.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-pot-management.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-recommendations.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-reports.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-subscriptions.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-3-track-causes-watering.jpg"></image>

Finalmente, se reorganizaron los eventos en torno a los agregados identificados. Esto permitió visualizar relaciones clave como:
- Qué comandos disparan qué eventos,
- Qué usuarios ejecutan qué comandos,
- Qué eventos activan políticas o modelos de lectura,

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-alerts.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-data-ingestion.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-iam.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-notifications.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-plant-management.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-plant-management.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-pot-management.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-recommendations.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-reports.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-subscriptions.jpg"></image>
<image src="../assets/img/capitulo-4/event-storming/iot-solution-software-design-event-storming-step-4-find-aggregates-&-re-sort-them-watering.jpg"></image>

<a href="https://miro.com/app/board/uXjVI7RMpGc=/?share_link_id=692821022758">Visualizar Miro</a>

#### 4.1.1.1 Candidate Context Discovery

En esta sección, el equipo describe detalladamente el proceso seguido para la sesión de Candidate Context Discovery, partiendo del modelo de dominio previamente construido mediante EventStorming, con el propósito de identificar y delimitar los Bounded Contexts que compondrán la arquitectura de Macetech. Según Khononov (2021), este enfoque estratégico de Domain‑Driven Design (DDD) requiere una combinación de análisis colaborativo y técnicas sistemáticas para aislar fragmentos del dominio que posean coherencia interna y aporten el mayor valor al negocio 

Para asegurar una exploración efectiva de los límites contextuales, se combinaron tres técnicas complementarias, tal como recomienda Khononov (2021):

* Start‑with‑Value: consiste en identificar primero aquellos subdominios o flujos de negocio cuyo impacto en la propuesta de valor sea más significativo, de modo que las decisiones de acotamiento prioricen las funcionalidades críticas para el usuario y el negocio 

* Start‑with‑Simple: implica descomponer el proceso principal en un conjunto mínimo de pasos secuenciales, desde el registro de usuario hasta la generación de recomendaciones, lo cual facilita la visualización y evita solapamientos entre candidatos de contexto 

* Look‑for‑Pivotal‑Events: se centra en detectar aquellos eventos de dominio que representan cambios de estado fundamentales, ya que estos hitos indefectiblemente marcan fronteras naturales entre contextos 

La sesión de Candidate Context Discovery, cuya duración no excedió las dos horas, se organizó como un taller interactivo en el que participaron todos los miembros de nuestro equipo de SevenSync, empleando una herramienta colaborativa de EventStorming, Miro. Durante la misma, se capturaron iterativamente pantallazos que documentan la evolución del modelo de eventos, desde la visión inicial hasta la estructuración final de los contextos. Estas imágenes se incorporarán en la sección para evidenciar la progresión metodológica y facilitar la trazabilidad de las decisiones tomadas.

A partir del modelo de dominio generado con EventStorming, el equipo explica y evidencia el proceso realizado para la sesión de Candidate Context Discovery, en la que se busca identificar los Bounded Contexts. Durante la sesión se siguieron estos pasos:

1. **Preparación y definición de alcance**

    Para garantizar una sesión estructurada y productiva, se llevaron a cabo las siguientes actividades previas:

    * Convocatoria y roles de los participantes

      Se conformó un grupo interdisciplinario bajo la coordinación de SevenSync, integrado por:
  
        - Desarrolladores backend y frontend, responsables de la viabilidad técnica.
    
        - Diseñadores UX/UI, encargados de asegurar la coherencia en la experiencia de usuario.

    * Definición de objetivos y alcance

      - **Propósito principal:** Descomponer el dominio de Macetech, desde el registro inicial del usuario hasta la emisión de recomendaciones y reportes personalizados.
  
      - **Alcance temporal:** Taller de mínimo dos horas y máximo tres horas en la plataforma Miro utilizando la técnica de EventStorming.

    * Herramientas y materiales de trabajo
  
      - Lienzo colaborativo en Miro: para la colocación y organización dinámica de eventos y comandos.
  
      - Post‑its codificados por color: diferenciando eventos de dominio, comandos de acción e integraciones externas.
  
      - Marcadores y cámaras: para anotar aclaraciones y capturar iteraciones de la evolución del modelo.
  
    * Asignación de responsabilidades
  
      - Facilitador: orientó la dinámica del taller, gestionó los tiempos y promovió la participación activa.
  
      - Escritor: trasladó al lienzo digital las notas y agrupaciones, asegurando la trazabilidad de cada modificación.
  
      - Expertos de dominio: validaron definiciones, aclararon términos y garantizaron la precisión del lenguaje ubicuo.

2. **Técnica Start‑with‑Value**

    Con el fin de enfocar el análisis en las áreas de mayor impacto, se realizó:

    * Identificación de “valores núcleo”
  
      Cada integrante propuso los flujos de negocio que, a su juicio, aportan el mayor valor a usuario y organización:
  
        - Gestión inicial de macetas y parámetros de configuración.
  
        - Generación de recomendaciones inteligentes para maximizar la tasa de éxito en el cuidado.
  
        - Monitoreo en tiempo real, evitando pérdidas derivadas de riegos inadecuados.
  
    * Priorización de eventos
  
      Se listaron todos los eventos detectados y se clasificaron según su impacto (alto, medio, bajo). Solo los catalogados como alto impacto se trasladaron a la siguiente etapa, garantizando que la sesión permaneciera centrada en las funciones críticas.

3. **Técnica Start‑with‑Simple**

    Para clarificar la secuencia de operaciones esenciales, se procedió a:

    *  Modelado visual con post‑its
 
       Cada uno de los nueve pasos se representó con post‑its de un único color, evitando superposiciones y facilitando la delimitación de responsabilidades entre los distintos subdominios.

    * Descomposición en pasos mínimos
  
      Se esbozó un timeline básico que recogiera el flujo de valor, compuesto por:

###### Tabla 40 y algo

*Flujo de valor identificado en el proceso de EventStorming de Macetech*

| Paso	| Descripción	| Artefactos de Dominio / Evento Pivotal |
|------|-------------|----------------------------------------|
| 1	| Registro del usuario en la plataforma.	| Comando: RegisterUser, Evento: UserRegistered |
| 2	| Creación de perfil con datos de contacto y preferencias.	|Comando: CreateProfile, Evento: ProfileCreated|
| 3	| Autenticación del usuario, incluyendo verificación 2FA.	|Comando: AuthenticateUser, Evento: UserAuthenticated|
| 4	| Pago de suscripción a Macetech (plan seleccionado).	|Comando: ProcessSubscriptionPayment, Evento: SubscriptionPaid|
| 5	| Registro y configuración inicial de la maceta (Pot).	|Comando: RegisterPot, Evento: PotRegistered|
| 6	| Definición de riego automático y programación de reportes periódicos.	|Comando: SelectWatering, Evento: AutomaticWateringProgrammed|
| 7	| Identificación de la planta asociada a la maceta (catálogo de especies).	|Comando: AddNewPlant, Evento: NewPlantAdded|
| 8	| Captura de datos de sensores (humedad, temperatura, pH, salinidad) y obtención de contexto climático vía API.	|SensorDataCollected + Evento: ExternalClimateDataFetched|
| 9	| Generación de recomendaciones y notificaciones de alertas.	|Comando: SelectRecommendation, Evento: RecommendationDisplayed|

4. **Técnica Look‑for‑Pivotal‑Events**

   Con el propósito de delimitar con precisión los contextos, se identificaron eventos de transición. Un evento de transición, según Khononov (2021), no solo marca un cambio de estado significativo, por ejemplo el paso de “usuario anónimo” a “usuario registrado” o de “maceta sin configurar” a “maceta lista para monitoreo”, sino que también permite priorizar de forma rigurosa el modelado y el desarrollo. Al centrarse en aquellos eventos de mayor impacto, el equipo puede determinar con claridad qué áreas requieren atención inmediata y cuáles funcionalidades deben implementarse primero, garantizando así que las decisiones de diseño estén siempre alineadas con los objetivos de negocio y el valor aportado al usuario.

###### Tabla 40 y algo

*Lista de transiciones identificadas en el proceso de EventStorming de Macetech*

| Transición | Descripción |
|--------------------|-------------|
| UserRegistered	| Un usuario anónimo se convierte en un usuario registrado, creando una cuenta válida en el sistema. | 
| UserProfileCreated	| Un usuario sin perfil asocia y configura su perfil con datos de contacto y preferencias personales. | 
| UserProfileDeleted	| Un usuario con perfil configurado elimina su perfil, quedando sin datos personales asociados. | 
| UserAuthenticated	| Una sesión no iniciada se valida exitosamente, incluyendo la verificación de dos factores (2FA). | 
| SubscriptionPaid	| Un usuario con plan inactivo activa su suscripción mediante el pago correspondiente, habilitando acceso a funcionalidades premium. | 
| SubscriptionCancelled	| Un usuario con suscripción activa cancela su plan, desactivando el acceso a servicios asociados. | 
| ExternalClimateDataFetched	| El sistema integra datos climáticos externos (vía API) según la ubicación del usuario, aportando contexto ambiental a los sensores. | 
| PotRegistered	| Una maceta previamente no asociada se registra y vincula a un usuario, quedando disponible para su gestión. | 
| PotSelected	| El usuario selecciona una maceta de la lista de macetas registradas, estableciéndola como activa para operaciones. | 
| PotDeleted	| El usuario elimina una maceta registrada, desvinculándola completamente de su cuenta. | 
| BluetoothDevicesPaired	| Se establece una conexión Bluetooth entre la maceta y la red del dispositivo, habilitando la comunicación inalámbrica. |
| IrrigationConfigured	| Una maceta sin parámetros de riego definidos adquiere reglas y periodicidad de riego configuradas. |
| PlantIdentified	| Se reconoce la especie de la planta en la maceta y se asignan rangos óptimos de riego, temperatura, pH y salinidad. |
| PlantRegistered	| Una planta identificada en maceta se vincula formalmente al usuario, completando su registro en el sistema. |
| PlantWatered	| Una planta con baja humedad recibe riego, aumentando su nivel de humedad a parámetros saludables. | 
| PlantDeleted	| El usuario elimina la asociación de la planta en la maceta, quedando ésta vacía nuevamente. | 
| WateringProgrammed	| Un sistema de riego manual se transforma en un programa de riego automático para la planta especificada. | 
| NotificationDisplayed	| El sistema muestra una notificación en la bandeja del usuario sobre un evento relevante (alerta, recomendación). | 
| NotificationChecked	| El usuario marca una notificación como leída, cambiando su estado a “checada” en la bandeja de notificaciones. | 
| NotificationDeleted	| El usuario elimina una notificación leída, removiéndola de la bandeja de notificaciones. |
| SensorDataCaptured	| Los sensores recaban datos brutos (humedad, temperatura, pH, salinidad) y los registran para su procesamiento. | 
| SensorDataDelivered	| Los datos capturados por los sensores se envían al sistema de la aplicación, quedando disponibles para el usuario. | 
| SensorDataCollected	| Un sensor pasa de no tener datos almacenados a disponer de registros de las métricas capturadas. |
| SensorHistoryDisplayed	| El sistema presenta al usuario el historial de datos de sensores, permitiendo aplicar filtros y explorar tendencias a lo largo del tiempo. |
| RecommendationGenerated	| Con los datos recopilados, el sistema elabora recomendaciones y alertas personalizadas para el usuario. |
| RecommendationDisplayed	| El usuario visualiza en su bandeja de recomendaciones las acciones sugeridas para optimizar el cuidado de su planta. | 
| ConsentDelivered	| El sistema muestra al usuario los documentos de términos y condiciones, dejando constancia de su presentación. |
| ConsentAccepted	| El usuario otorga su consentimiento a los términos y condiciones, registrándose dicha aceptación en el sistema. |
| ConsentRejected	| El usuario rechaza los términos y condiciones, registrándose dicha negativa en el sistema. |

  * Agrupación por afinidad de eventos

    Sobre el lienzo, los post‑its se reagruparon alrededor de cada evento pivotal, permitiendo visualizar con claridad los límites naturales entre posibles contextos.

5. Visualización evolutiva

    Para documentar el progreso y facilitar la trazabilidad:

    * Capturas iterativas

    Se realizaron screenshots en Miro cada 30 minutos, mostrando:

     - Estado inicial: eventos sin ordenar.
   
     - Tras Start‑with‑Value: solo eventos de alto impacto.
   
     - Tras Start‑with‑Simple: disposición cronológica.
   
     - Tras Look‑for‑Pivotal‑Events: primeros agrupamientos.
   
     - Versión final: consolidación de los candidatos a contextos.

    * Registro meticuloso
    
  Cada imagen se anotó con fecha, hora y una breve descripción de los ajustes realizados, asegurando que el informe refleje con exactitud la evolución metodológica, y facilitando la inclusión de estas evidencias en la sección correspondiente.

6. Candidatos a Bounded Context

A continuación presentamos la sección de Candidatos a Bounded Contexts, donde listamos todos los contextos identificados en la sesión inicial (incluyendo aquellos que finalmente no se consolidaron) y la justificación de su inclusión o exclusión en el conjunto definitivo.

###### Tabla 40 y algo

*Lista de candidatos a Bounded Context identificados en el proceso de EventStorming de Macetech*

| Contexto	| Responsabilidades clave	| ¿Pasa al diseño final? |
|----------|-------------------------|------------------------|
| IAM	| Autenticación (login/logout, manejo de sesiones), emisión y validación de JWT y tokens de refresco, soporte 2FA, gestión de permisos y roles	| **Consolidado:** La seguridad y control de acceso son requisitos no negociables. Al agrupar login, emisión de tokens y 2FA en un único contexto, se garantiza la consistencia en la gestión de credenciales, la separación de responsabilidades y la escalabilidad de las políticas de acceso. Además, comparte modelo con “User Management” para evitar duplicación de lógica de usuario. |
| Account Management	| CRUD de cuentas de usuario, eliminación, recuperación de contraseña, validación de datos de contacto	| **Consolidado:** Es el núcleo del ciclo de vida de cuentas de usuario. Centralizar creación, actualización y baja de cuentas asegura trazabilidad de eventos y facilita la auditoría. Al estar separado de IAM, mantiene independencia entre identidad y gestión de recursos de usuario. |
| Profile & Personal Data |	Almacenamiento/actualización de datos de perfil, preferencias, integración Geo API, normalización de direcciones	| **Consolidado:** Ofrece personalización y localización sin contaminar otros contextos. Al abstraer el manejo de datos de contacto y preferencias, se optimiza la reutilización de la Geo API y se garantiza que las modificaciones de esquema o validaciones no afecten la lógica de negocio de autenticación ni de facturación. 
| Pot Management	| CRUD de macetas, configuración de parámetros de riego (frecuencia, volumen, límites), metadatos (nombre, ID), persistencia histórica	| **Consolidado:** Es la base de la capa IoT: registrar macetas y sus parámetros iniciales. Aglutinar aquí la configuración básica permite desacoplar la lógica de riego y la lógica de planta, favoreciendo la extensibilidad hacia nuevos tipos de dispositivo sin impactar módulos de control ni de analítica. |
| Plant Management |	Catálogo de especies (PlantSpecies), rangos óptimos (pH, luminosidad, temperatura, salinidad), validación planta–maceta | **Consolidado:** Permite evolucionar el modelo botánico de forma independiente al hardware. Separar la lógica de especies y rangos óptimos facilita incorporar nuevas plantas o proveedores de datos externos, y garantiza que la capa de riego no dependa de cambios en el catálogo ni en los esquemas de las APIs externas. |
| Watering Management	| Motor de decisión de riego (análisis de SensorData + PotConfiguration), generación de trabajos de riego (IrrigationJob), manejo de excepciones, coordinación con IoT |	**Consolidado:** Aísla la complejidad del control físico del riego. Distinguirlo de la gestión de activos (Pot Management) permite evolucionar algoritmos de riego y protocolos IoT sin afectar el modelado de macetas o plantas, mejorando el rendimiento y el despliegue independiente de servicios de control. |
| Subscriptions & Payments	| Definición y gestión de planes (SubscriptionPlan), procesamiento de transacciones, gestión de facturas (Invoice), integración con pasarelas y webhooks. | **Consolidado:** Soporta el modelo de negocio freemium/pago. Mantener un contexto dedicado a facturación garantiza que cambios en pasarelas, planes o flujos de cobro no afecten la lógica de usuario ni de riego. La separación da flexibilidad para adaptar políticas de precio y métodos de pago con mínima fricción. |
| System Monitoring & Control |	Health checks, registro de logs críticos, generación/envío de alertas (push, email, SMS), dashboard operativo. | **Consolidado:** Integra supervisión y notificaciones en un único lugar, evitando fragmentar la lógica de alertas. Concentra la detección de fallos y la notificación al usuario o al equipo de operaciones, garantizando coherencia en umbrales y canales de comunicación, y favoreciendo la medición de uptime. |
| Data Insights & Reporting | Ingesta, normalización y almacenamiento de SensorRecord; procesamiento batch/stream; dashboards	| **Consolidado:** Proporciona visibilidad de operación y resultados. Mantenerlo separado de la capa de control permite escalar pipelines de datos y ajustar retención sin impactar los servicios transaccionales, favoreciendo la adopción de nuevas herramientas de analítica. |
| Caring Intelligence	| Motor de recomendaciones, generación de Recommendation, reportes personalizados (ReportTemplate), aprendizaje continuo. | **Consolidado:** Corazón del valor añadido de Macetech. Al separar el procesamiento de la ingesta de datos, se posibilita iterar en modelos de reglas de negocio sin afectar flujos de riego ni analítica básica, y se facilita la experimentación y el versionado de algoritmos. |
| Notifying System	| Envío y gestión de notificaciones genéricas	sin información adicional o relacionada a recomendaciones o alertas | **Excluido:** Su responsabilidad acotada (solo envíos) carecía de un modelo de datos robusto y se solapaba con alertas críticas. Se integró dentro de System Monitoring & Control para centralizar tanto la supervisión como los canales de comunicación y evitar duplicación de lógica. | 
| Critical Alert System |	Detección y disparo de alertas críticas según umbrales muy concretos para las métricas de las plantas |	**Excluido:** Solapaba responsabilidades con el contexto de monitoreo general y carecía de un dominio propio (no gestionaba datos ni reglas de negocio distintos). Su funcionalidad se migró a System Monitoring & Control, que unifica alertas de todo tipo. |
| AI Service | Servicio genérico de IA para procesamiento de datos sin enfoque claro	en las recomendaciones de cada planta y las alertas no definidas | **Excluido:** Era excesivamente genérico y no alineado con casos de uso concretos o con los propios ideales del proyecto. Se reemplazó por integraciones enfocadas: Plant Management usa Plant API y Caring Intelligence alberga la lógica de recomendaciones y aprendizaje automático plenamente contextualizadas. |
| SensorState	| Gestión de estados físicos del sensor (calibración, fallos, ciclos de vida)	de forma remota. | **Excluido:** La complejidad de manejar calibraciones y ciclos de vida requería un dominio especializado de ingeniería de hardware. Decidimos evitar la complejidad de este Bounded Context para no perder nuestro enfoque en el software y el funcionamiento del propio sistema IoT. |

7. Bounded Contexts finales

Como resultado de la sesión de Candidate Context Discovery y con base en los eventos pivotal identificados, se definieron y refinaron los siguientes diez Bounded Contexts ante todos los candidatos iniciales. Cada uno incluye sus responsabilidades principales, lenguaje ubicuo y contratos de integración.

###### Tabla 40 y algo

*Lista de Bounded Context finales identificados en el proceso de EventStorming de Macetech*

| Contexto  | Responsabilidades clave   | Ubiquitous Language    |
|-----------|---------------------------|------------------------|
| **1. IAM**                       | - Autenticación de usuarios (login/logout, manejo de sesiones) <br> - Emisión y validación de JSON Web Tokens (JWT) y tokens de refresco  - Soporte de 2FA (envío y verificación de códigos) <br> - Gestión de permisos y roles | User, Credentials, Session, Token, 2FA |
| **2. Account Management**           | - Operaciones CRUD sobre entidades **User** <br> - Eliminación (soft/hard delete) de cuentas  <br>  - Recuperación de contraseña y gestión de **PasswordRecoveryToken** <br>  - Validación de datos de contacto y cumplimiento de políticas de seguridad  | User, PasswordRecoveryToken, AccountStatus |
| **3. Profile & Personal Data**   | - Almacenamiento y actualización de datos de perfil (nombres, teléfono, dirección) <br>  - Gestión de preferencias de usuario (idioma, notificaciones)  <br>  - Integración con **Geo API** para catálogo de países y ciudades <br>  - Normalización y validación de direcciones  | Profile, Address, PhoneNumber, Preference, Country   |                                                                                                 |
| **4. Pot Management** | - Operaciones CRUD sobre la entidad **Pot** <br><br> - Configuración de parámetros de riego (frecuencia, volumen, thresholds) <br>  - Gestión de metadatos (nombre, identificador único, etiquetas) <br>  - Persistencia de configuraciones históricas para auditoría | Pot, PotConfiguration, Threshold  |
| **5. Plant Management**          | - Catálogo de especies vegetales (**PlantSpecies**): atributos técnicos y rangos óptimos (pH, luminosidad, temperatura, salinidad) <br> - Validación de compatibilidad planta–maceta <br>  - Sincronización periódica con APIs externas para actualizar parámetros y nuevas especies     | PlantSpecies, OptimalRange, Compatibility  |                                                                                                |
| **6. Watering Management**       | - Motor de decisión para riego: análisis de **SensorData** y parámetros de **PotConfiguration** <br> - Generación de **IrrigationJob** (planificación y disparo de válvulas) <br> - Manejo de excepciones de hardware (fallos, reintentos)  <br> - Coordinación con servicios de control de dispositivos IoT  | IrrigationJob, ValveCommand, SensorData               |                                                                                          |
| **7. Subscriptions & Payments**  | - Definición y gestión de **SubscriptionPlan** <br> - Procesamiento de transacciones recurrentes y cobros únicos <br>  - Gestión de **Invoice** y seguimiento de estado de pago <br>  - Integración con pasarelas externas y webhooks  | SubscriptionPlan, Invoice, PaymentTransaction  |                             
| **8. System Monitoring & Control** | - Supervisión del estado de servicios y componentes (`health checks`) <br> - Registro y almacenamiento de logs críticos <br>  - Generación y envío de alertas (push, email, SMS) ante umbrales o fallos <br> - Dashboard operativo para visualización de métricas de disponibilidad | SystemHealth, Alert, NotificationChannel |  
| **9. Data Insights & Reporting** | - Ingesta, normalización y almacenamiento de **SensorRecord**  <br> - Procesamiento batch/stream para generación de métricas agregadas  <br> - Exposición de dashboards y endpoints de consulta  <br> - Exportación de datos a formatos CSV/JSON para análisis externo   | SensorRecord, InsightReport, Dashboard   |                 
| **10. Caring Intelligence**      | - Motor de recomendación basado en reglas y modelos ML/IA  <br> - Generación de **Recommendation** y mapeo a patrones de usuario  <br> - Creación de reportes personalizados (**ReportTemplate**)  <br> - Aprendizaje continuo a partir de retroalimentación del usuario   | Recommendation, ReportTemplate, Rule, Feedback  |  

#### 4.1.1.2 Domain Message Flows Modeling.

#### 4.1.1.3 Bounded Context Canvases.
### Identity and Access Management
<image src="../assets/img/capitulo-4/bounded-context-canvases/iam.png"></image>
### Profile and Personal Data
<image src="../assets/img/capitulo-4/bounded-context-canvases/profile-and-personal-data.png"></image>
### Pot Management
<image src="../assets/img/capitulo-4/bounded-context-canvases/pot-management.png"></image>
### Plant Management
<image src="../assets/img/capitulo-4/bounded-context-canvases/plant-management.png"></image>
### System Monitoring & Control
<image src="../assets/img/capitulo-4/bounded-context-canvases/system-monitoring-and-control.png"></image>

### 4.1.2. Context Mapping.

### 4.1.3. Software Architecture.

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

| Propiedad   | Valor                         |
|-------------|-------------------------------|
| **Nombre**  | User                          |
| **Categoría** | Aggregate Root             |
| **Propósito** | Almacenar datos del usuario |

---

### Atributos

| Nombre       | Tipo de dato   | Visibilidad | Descripción                                  |
|--------------|----------------|-------------|----------------------------------------------|
| Id           | `unsigned long`| private     | Identificador irrepetible del usuario        |
| FullName     | `FullName`     | private     | Nombres del usuario                          |
| Email        | `Email`        | private     | Correo electrónico del usuario               |
| Password     | `PasswordHash` | private     | Lógica de hashing/verificación de contraseña |
| Role         | `List<Role>`   | private     | Rol del usuario                              |
| CreatedDate  | `DateTime`     | private     | Fecha de creación del usuario                |
| Status       | `Status` (enum)| private     | Estado del usuario                           |

---

### Métodos

| Nombre         | Tipo de retorno | Visibilidad | Descripción                            |
|----------------|-----------------|-------------|----------------------------------------|
| ChangeName     | `void`          | public      | Cambiar nombre del usuario             |
| ChangeEmail    | `void`          | public      | Cambiar correo electrónico del usuario |
| ChangePassword | `void`          | public      | Cambiar contraseña del usuario         |
| ChangeRole     | `void`          | public      | Cambiar el rol del usuario             |
| Suspend        | `void`          | public      | Suspender al usuario                   |
| Activate       | `void`          | public      | Reactiva al usuario                    |
| Delete         | `void`          | public      | Marcar al usuario como eliminado       |

## UserId

| Propiedad    | Valor                                         |
|--------------|-----------------------------------------------|
| **Nombre**   | UserId                                        |
| **Categoría**| Value Object                                  |
| **Propósito**| Encapsular el identificador único de usuario  |

### Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción                         |
|--------|--------------|-------------|-------------------------------------|
| Value  | `Long`       | private     | Identificador único de usuario      |

---

## FullName

| Propiedad    | Valor                                   |
|--------------|-----------------------------------------|
| **Nombre**   | FullName                                |
| **Categoría**| Value Object                            |
| **Propósito**| Almacenar nombres de usuario            |

### Atributos

| Nombre     | Tipo de dato | Visibilidad | Descripción               |
|------------|--------------|-------------|---------------------------|
| name       | `string`     | private     | Nombre del usuario        |
| LastNames  | `string`     | private     | Apellidos del usuario     |

---

## Email

| Propiedad    | Valor                                  |
|--------------|----------------------------------------|
| **Nombre**   | Email                                  |
| **Categoría**| Value Object                           |
| **Propósito**| Almacenar el correo electrónico del usuario |

### Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción                   |
|--------|--------------|-------------|-------------------------------|
| Email  | `string`     | private     | Correo electrónico del usuario |

## PasswordHash

| Propiedad    | Valor                                              |
|--------------|----------------------------------------------------|
| **Nombre**   | PasswordHash                                       |
| **Categoría**| Value Object                                       |
| **Propósito**| Almacenar el correo electrónico del usuario        |

### Atributos

| Nombre | Tipo de dato | Visibilidad | Descripción                         |
|--------|--------------|-------------|-------------------------------------|
| email  | `string`     | private     | Correo electrónico del usuario      |

### Métodos

| Nombre  | Tipo de retorno | Visibilidad | Descripción                                       |
|---------|-----------------|-------------|---------------------------------------------------|
| Matches | `bool`          | public      | Verificar si un texto coincide con este hash      |

---

## UserFactory

| Propiedad    | Valor                                      |
|--------------|--------------------------------------------|
| **Nombre**   | UserFactory                                |
| **Categoría**| Factory                                    |
| **Propósito**| Crear nuevas instancias de `User`          |

### Métodos

| Nombre | Tipo de retorno | Visibilidad | Descripción                      |
|--------|-----------------|-------------|----------------------------------|
| Create | `User`          | public      | Crear una instancia de `User`    |

## IUserRepository

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | IUserRepository                           |
| **Categoría** | Repository                                |
| **Propósito** | Persistir y consultar entidades de User   |

### Métodos

| Nombre               | Tipo de retorno | Visibilidad | Descripción                                                   |
|----------------------|-----------------|-------------|---------------------------------------------------------------|
| GetByIdAsync         | `User?`         | public      | Obtener un usuario por identificador                          |
| FindByEmailAsync     | `User?`         | public      | Buscar un usuario por correo                                  |
| ExistsByEmailAsync   | `bool`          | public      | Verificar si hay un usuario con dicho email ya registrado     |
| FindAllAsync         | `List<User>`    | public      | Lista de usuarios (para casos de administración)              |
| SaveAsync            | `User`          | public      | Crear o actualizar un usuario; devuelve la entidad persistida |
| DeleteLogicallyAsync | `bool`          | public      | Elimina lógicamente un usuario                                |
| CountAsync           | `long`          | public      | Total de usuarios                                             |

---

## ISessionRepository

| Propiedad     | Valor                                       |
|---------------|---------------------------------------------|
| **Nombre**    | ISessionRepository                          |
| **Categoría** | Repository                                  |
| **Propósito** | Persistir y consultar entidades de User     |

### Métodos

| Nombre                  | Tipo de retorno   | Visibilidad | Descripción                                      |
|-------------------------|-------------------|-------------|--------------------------------------------------|
| FindByTokenId           | `SessionToken?`   | public      | Obtener un SessionToken por identificador        |
| Store                   | `void`            | public      | Guardar un SessionToken activo                   |
| Revoke                  | `void`            | public      | Revocar un token                                 |
| RevokeAllSessionForUser | `void`            | public      | Revocar todas los SessionToken de un usuario     |

## Authenticator

| Propiedad     | Valor                                        |
|---------------|----------------------------------------------|
| **Nombre**    | Authenticator                                |
| **Categoría** | Domain Service                               |
| **Propósito** | Verificar las credenciales de un usuario     |

### Métodos

| Nombre       | Tipo de retorno  | Visibilidad | Descripción                  |
|--------------|------------------|-------------|------------------------------|
| authenticate | `SessionToken`   | public      | Valida las credenciales de un usuario y devuelve un token de sesión |

---

## SessionToken

| Propiedad     | Valor                                          |
|---------------|------------------------------------------------|
| **Nombre**    | SessionToken                                   |
| **Categoría** | Entity                                         |
| **Propósito** | Representar una sesión activa de un usuario     |

### Atributos

| Nombre      | Tipo de dato | Visibilidad | Descripción                                 |
|-------------|--------------|-------------|---------------------------------------------|
| TokenId     | `string`     | private     | Identificador único del token               |
| userId      | `UserId`     | private     | Identificador del usuario                   |
| createdAt   | `DateTime`   | private     | Fecha y hora de creación del token          |
| expiresAt   | `DateTime`   | private     | Fecha y hora de expiración del token        |
| revoked     | `bool`       | private     | Indica si el token ha sido revocado         |

#### 4.2.1.2. Interface Layer.

## UserController

| Propiedad     | Valor                   |
|---------------|-------------------------|
| **Nombre**    | UserController          |
| **Categoría** | Controller              |
| **Propósito** | Gestionar usuarios      |
| **Ruta**      | `/api/users`            |

### Métodos

| Nombre         | Ruta                    | Acción                      | Handle                                           |
|----------------|-------------------------|-----------------------------|--------------------------------------------------|
| GetById        | `/{userId}`             | Obtiene información del usuario | `GetUserByIdQuery`                              |
| ChangeName     | `/{userId}/name`        | Cambia `FullName`           | `ChangeUserNameCommand`                          |
| ChangeEmail    | `/{userId}/email`       | Cambia `Email`              | `ChangeUserEmailCommand`                         |
| ChangePassword | `/{userId}/password`    | Cambia `PasswordHash`       | `ChangeUserPasswordCommand`                      |
| ChangeStatus   | `/{userId}/status`      | Cambia `Status`             | `ActivateUserCommand`, `SuspendUserCommand`, `DeleteUserCommand` |

---

## AuthController

| Propiedad     | Valor                                                                 |
|---------------|-----------------------------------------------------------------------|
| **Nombre**    | AuthController                                                        |
| **Categoría** | Controller                                                            |
| **Propósito** | Encargado de todo lo relacionado con registro y autenticación         |
| **Ruta**      | `/api/auth`                                                           |

### Métodos

| Nombre   | Ruta         | Acción                                    | Handle                     |
|----------|--------------|-------------------------------------------|----------------------------|
| Register | `/register`  | Crea un nuevo usuario                     | `RegisterUserCommand`      |
| Login    | `/login`     | Valida credenciales y devuelve token      | `LoginUserCommand`         |
| Refresh  | `/refresh`   | Renueva el acceso; nuevo token            | `~`                        |
| Logout   | `/logout`    | Revoca el token activo                    | `RevokeSessionCommand`     |

#### 4.2.1.3. Application Layer.


## UserRegisterCommandHandler

| Propiedad     | Valor                        |
|---------------|------------------------------|
| **Nombre**    | UserRegisterCommandHandler   |
| **Categoría** | Command Handler             |
| **Propósito** | Registrar un usuario         |
| **Comando**   | RegisterUserCommand          |

---

## UserLoginCommandHandler

| Propiedad     | Valor                      |
|---------------|----------------------------|
| **Nombre**    | UserLoginCommandHandler    |
| **Categoría** | Command Handler           |
| **Propósito** | Iniciar sesión a un usuario|
| **Comando**   | LoginUserCommand           |

---

## UserLogoutCommandHandler

| Propiedad     | Valor                       |
|---------------|-----------------------------|
| **Nombre**    | UserLogoutCommandHandler    |
| **Categoría** | Command Handler            |
| **Propósito** | Cerrar sesión de un usuario |
| **Comando**   | LogoutUserCommand           |

---

## RegisteredUserEventHandler

| Propiedad     | Valor                    |
|---------------|--------------------------|
| **Nombre**    | RegisteredUserEventHandler |
| **Categoría** | Event Handler           |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserRegisteredEvent     |

---

## UserLoggedInEventHandler

| Propiedad     | Valor                        |
|---------------|------------------------------|
| **Nombre**    | UserLoggedInEventHandler     |
| **Categoría** | Event Handler              |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserLoggedInEvent           |

---

## UserLoggedOutEventHandler

| Propiedad     | Valor                               |
|---------------|-------------------------------------|
| **Nombre**    | UserLoggedOutEventHandler           |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserLoggedOutEvent                  |

#### 4.2.1.4. Infrastructure Layer.


## UserRepository

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | UserRepository                            |
| **Categoría** | Repositorio                               |
| **Propósito** | Persistir y consultar entidades de `User` |
| **Interfaz**  | `IUserRepository`                        |

---

## SessionRepository

| Propiedad     | Valor                                       |
|---------------|---------------------------------------------|
| **Nombre**    | SessionRepository                           |
| **Categoría** | Repositorio                                 |
| **Propósito** | Persistir y consultar entidades de `User`   |
| **Interfaz**  | `ISessionRepository`                       |

---

## AppDbContext

| Propiedad     | Valor                                          |
|---------------|------------------------------------------------|
| **Nombre**    | AppDbContext                                   |
| **Categoría** | ORM Context                                    |
| **Propósito** | Punto central de acceso a la base de datos     |

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

<image src="../assets/img/capitulo-4/bounded-context-plant-registration/database-diagram.png"></image>

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

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-1.jpg"></image>

- Fase 2: Refinamiento de Domain Events

En una segunda ronda colaborativa, se depuraron los eventos recolectados: se eliminaron duplicados, se aclararon ambigüedades y se reorganizaron cronológicamente. También se discutió la terminología para asegurar coherencia y precisión semántica.

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-2.jpg"></image>


<image src="../assets/img/capitulo-4/event-storming/event-storming-step-2.jpg"></image>

Fase 3: Rastrear las Causas: Durante esta fase, se analizaron los eventos para identificar sus causas. Se consideraron cuatro tipos principales de disparadores:
- Acciones de usuarios (comandos, actores, vistas),
- Sistemas externos,
- Procesos de negocio (por ejemplo, condiciones temporales),
- Otros eventos del dominio (reacciones automáticas).


<image src="../assets/img/capitulo-4/event-storming/event-storming-step-3-key.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-3-part-1.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-3-part-2.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-3-part-3.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-3-part-4.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-3-part-5.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-3.jpg"></image>


Finalmente, se reorganizaron los eventos en torno a los agregados identificados. Esto permitió visualizar relaciones clave como:
- Qué comandos disparan qué eventos,
- Qué usuarios ejecutan qué comandos,
- Qué eventos activan políticas o modelos de lectura,

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-1.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-2.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-3.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-4.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-5.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-6.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-7.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-8.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-9.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4-part-10.jpg"></image>

<image src="../assets/img/capitulo-4/event-storming/event-storming-step-4.jpg"></image>

<a href="https://miro.com/app/board/uXjVI7RMpGc=/?share_link_id=692821022758">Visualizar Miro</a>

#### 4.1.1.1 Candidate Context Discovery.

Tras finalizar la sesión de EventStorming, el equipo procedió a la fase de Candidate Context Discovery, cuyo objetivo principal es identificar los posibles Bounded Contexts del sistema. Esta actividad permite avanzar hacia una estructura modular del software alineada con los límites naturales del dominio del negocio.

Según Vernon (2013), “definir correctamente los Bounded Contexts es clave para evitar ambigüedades semánticas, promover la autonomía de los equipos y mantener la cohesión del modelo en crecimiento”. Para este análisis se aplicaron diversas técnicas de segmentación que facilitaron la identificación progresiva de contextos candidatos a partir de los eventos descubiertos.

#### 4.1.1.2 Domain Message Flows Modeling.

#### 4.1.1.3 Bounded Context Canvases.

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

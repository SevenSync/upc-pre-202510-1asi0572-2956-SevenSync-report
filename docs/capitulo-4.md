# Capítulo IV: Solution Software Design

## 4.1. Strategic-Level Domain-Driven Design.

### 4.1.1. EventStorming.

#### 4.1.1.1 Candidate Context Discovery.

#### 4.1.1.2 Domain Message Flows Modeling.

#### 4.1.1.3 Bounded Context Canvases.

### 4.1.2. Context Mapping.

### 4.1.3. Software Architecture.

#### 4.1.3.1. Software Architecture System Landscape Diagram.

#### 4.1.3.2. Software Architecture Context Level Diagrams.

#### 4.1.3.2. Software Architecture Container Level Diagrams.

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
<image src=../assets/bounded-context-iam/components-diagram.png></image>

#### 4.2.1.6. Bounded Context Software Architecture Code Level Diagrams.

##### 4.2.1.6.1. Bounded Context Domain Layer Class Diagrams.
<image src=../assets/bounded-context-iam/class-diagram.png></image>

##### 4.2.1.6.2. Bounded Context Database Design Diagram.
<image src=../assets/bounded-context-iam/database-diagram.png></image>

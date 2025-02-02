
 ForoHub

ForoHub es una API REST desarrollada en Java utilizando Spring Boot. La aplicación gestiona tópicos de discusión en un foro, proporcionando funcionalidades de creación, listado, actualización, eliminación y autenticación mediante tokens JWT.

Requisitos del Proyecto

Java: 17 o superior.

Spring Boot: 3.x.

Maven: 4.x.

Base de Datos: MySQL.

Dependencias Utilizadas

Spring Web: Para crear endpoints REST.

Spring Data JPA: Para la interacción con la base de datos.

MySQL Driver: Para la conexión con la base de datos.

Flyway Migration: Para gestionar migraciones de esquema.

Spring Security: Para implementar autenticación y autorización.

Lombok: Para simplificar la escritura de código.

JWT (JSON Web Token): Para la autenticación basada en tokens.

Funcionalidades de la API

1. Gestión de Tópicos

Crear Tópico:

Endpoint: POST /tópicos

Requiere autenticación.

Datos: Título, mensaje, autor, curso.

Listar Tópicos:

Endpoint: GET /tópicos

Opcionales:

Ordenar por fecha de creación.

Filtrar por curso y año.

Paginación.

Actualizar Tópico:

Endpoint: PUT /tópicos/{id}

Requiere autenticación.

Eliminar Tópico:

Endpoint: DELETE /tópicos/{id}

Requiere autenticación.

2. Autenticación y Autorización

Generación de Tokens JWT:

Endpoint: POST /login

Requiere datos de usuario y contraseña.

Control de Acceso:

Todas las rutas protegidas requieren un token válido en el encabezado de las solicitudes.

Estructura del Proyecto

src/main/java
├── com.tuempresa.foro
│   ├── controller
│   │   ├── TopicoController.java
│   │   └── AuthController.java
│   ├── dto
│   │   └── TopicoDTO.java
│   ├── entity
│   │   └── Topico.java
│   ├── repository
│   │   └── TopicoRepository.java
│   ├── service
│   │   ├── TopicoService.java
│   │   └── TokenService.java
│   └── security
│       ├── SecurityConfigurations.java
│       └── JWTFilter.java
├── resources
│   ├── application.properties
│   └── db/migration/V1__Create_Topicos_Table.sql

Configuración del Proyecto

Clonar el Repositorio

git clone <URL_DEL_REPOSITORIO>
cd ForoHub

Configurar la Base de Datos

Actualizar application.properties con tus credenciales de MySQL.

spring.datasource.url=jdbc:mysql://localhost:3306/foro_db
spring.datasource.username=tu_usuario
spring.datasource.password=tu_contraseña
spring.jpa.hibernate.ddl-auto=validate
spring.flyway.enabled=true

Migraciones con Flyway

Flyway ejecutará automáticamente los scripts SQL en src/main/resources/db/migration para crear las tablas necesarias.

Compilar y Ejecutar

mvn clean install
mvn spring-boot:run

Pruebas con Insomnia o Postman

Generar Token:

Endpoint: POST /login

Body:

{
  "username": "usuario",
  "password": "contraseña"
}

Copiar el token recibido.

Acceder a Endpoints Protegidos:

Agregar el token al encabezado de autorización:


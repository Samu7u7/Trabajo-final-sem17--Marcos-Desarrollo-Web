StreamsUTP
Descripción del Proyecto
StreamsUTP es una plataforma web desarrollada con Spring Boot que permite a los usuarios explorar, alquilar y comprar películas, gestionar su historial de órdenes y administrar perfiles. Incluye funcionalidades de administración para usuarios y ventas, y una interfaz de usuario intuitiva construida con Thymeleaf y Bootstrap.

Características Clave
Autenticación y Autorización:

Registro e inicio de sesión de usuarios.

Roles de usuario (USER y ADMIN) con acceso diferenciado a funcionalidades.

Spring Security para gestionar la seguridad de la aplicación.

Gestión de Películas:

Visualización del catálogo de películas.

Opciones de compra y alquiler para cada película.

API RESTful (/api/peliculas) para la gestión de películas (CRUD) accesible por administradores.

Carrito de Compras:

Añadir películas al carrito con opciones de compra o alquiler.

Visualizar y gestionar elementos en el carrito.

Proceso de pago simulado con tarjeta de crédito.

Historial de Órdenes:

Los usuarios pueden ver un historial detallado de sus órdenes.

Administración de órdenes por parte de los administradores.

Perfiles de Usuario:

Visualización del perfil de usuario, incluyendo información personal y plan.

Funcionalidades de administración de usuarios (CRUD) para administradores.

Notificaciones:

Mensajes de éxito y error visibles para el usuario en diversas operaciones.

Tecnologías Utilizadas
Backend
Spring Boot: Framework principal para el desarrollo de aplicaciones Java.

Spring Security: Para la gestión de autenticación y autorización.

Spring Data JPA: Simplifica el acceso a datos y las operaciones de base de datos.

Hibernate: Implementación de JPA para mapeo objeto-relacional.

Maven: Herramienta de automatización de construcción y gestión de dependencias.

Base de Datos
MySQL: Base de datos relacional para almacenar toda la información de la aplicación.

Frontend
Thymeleaf: Motor de plantillas para renderizar vistas HTML dinámicas.

Bootstrap 5: Framework CSS para un diseño responsivo y moderno.

JavaScript: Para interacciones del lado del cliente y lógica dinámica.

Font Awesome: Para iconos escalables.

Requisitos del Sistema
Para compilar y ejecutar este proyecto, necesitas tener instalado:

Java Development Kit (JDK): Versión 17 o superior.

Apache Maven: Versión 3.6.0 o superior.

MySQL Server: Versión 8.0 o superior.

Configuración de la Base de Datos
El archivo src/main/resources/application.properties contiene la configuración de la base de datos:

Properties

spring.datasource.
=jdbc:mysql://localhost:3306/streamsutpdb?createDatabaseIfNotExist=true&useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=CARBajal281?? # ¡IMPORTANTE: CAMBIA ESTA CONTRASEÑA POR LA TUYA!
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.thymeleaf.mode=HTML
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
spring.jpa.hibernate.naming.physical-strategy=org.hibernate.boot.model.naming.PhysicalNamingStrategyStandardImpl
logging.level.org.springframework.security=DEBUG
Antes de ejecutar la aplicación:

Asegúrate de que tu servidor MySQL esté en ejecución.

La propiedad createDatabaseIfNotExist=true en la URL JDBC intentará crear la base de datos streamsutpdb si no existe. Asegúrate de que el usuario root (o el usuario configurado) tenga los permisos necesarios para crear bases de datos.

Cambia CARBajal281?? por la contraseña real de tu usuario root de MySQL.

Credenciales de Administrador 
Para acceder al panel de administración y las APIs protegidas, puedes usar las siguientes credenciales:

Usuario: adminLOL

Contraseña: admin2814001 

Ejecución del Proyecto
Sigue estos pasos para levantar la aplicación:

Clonar el repositorio:

Bash

git clone <https://github.com/Samu7u7/Trabajo-final-sem17--Marcos-Desarrollo-Web>
cd streamsutp

Compilar el proyecto con Maven:

Bash

mvn clean install
Esto descargará todas las dependencias y construirá el archivo .jar ejecutable.

Ejecutar la aplicación Spring Boot:

Bash

mvn spring-boot:run
O, si prefieres ejecutar el JAR compilado:

Bash

java -jar target/streamsutp-0.0.1-SNAPSHOT.jar # El nombre del archivo JAR puede variar ligeramente
La aplicación estará disponible en http://localhost:8080.

Endpoints de la API (Solo para Administradores)
La aplicación expone una API RESTful para la gestión de películas, que está protegida con Spring Security y requiere autenticación Basic (ROLE_ADMIN).

POST /api/peliculas

Descripción: Crea una nueva película.

Requiere: Autenticación ROLE_ADMIN.

Cuerpo de la solicitud (JSON):

JSON

{
  "titulo": "Título de la película",
  "imagen": "/ruta/a/imagen.jpg",
  "precioAlquilar": 5.99,
  "precioComprar": 19.99
}
GET /api/peliculas

Descripción: Obtiene una lista de todas las películas.

No requiere autenticación (accesible públicamente).

GET /api/peliculas/{id}

Descripción: Obtiene los detalles de una película específica por su ID.

No requiere autenticación (accesible públicamente).

DELETE /api/peliculas/{id}

Descripción: Elimina una película por su ID.

Requiere: Autenticación ROLE_ADMIN.

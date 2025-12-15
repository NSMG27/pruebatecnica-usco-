\# PRUEBA TÉCNICA – SISTEMA DE GESTIÓN DE TRÁMITES

\## 📌 Descripción general

Sistema web para la \*\*gestión y seguimiento de trámites\*\*, desarrollado como prueba técnica. La solución está compuesta por un \*\*backend en Spring Boot\*\*, siguiendo principios de \*\*Domain Driven Design (DDD)\*\*, y un \*\*frontend moderno desacoplado\*\*, con autenticación \*\*JWT stateless\*\*.

\---

\## 🧱 Stack tecnológico

\### Backend

- \*\*Java 17\*\*
- \*\*Spring Boot\*\*
- \*\*Spring Security\*\* (JWT)
- \*\*Spring Data JPA / Hibernate\*\*
- \*\*Arquitectura DDD\*\*
- \*\*Base de datos\*\*: MySQL 8 (H2 opcional para pruebas)

\### Frontend

- \*\*Node.js 18+\*\*
- Framework frontend moderno
- Consumo de API REST

\---

\## ▶️ Ejecución del Backend

\### Requisitos

- Java 17 o superior
- Maven 3.8 o superior
- MySQL 8 (opcional H2)
- Git

\### Pasos

1. Clonar el repositorio

\```bash

git clone https://github.com/NSMG27/pruebatecnica-usco.git

Entrar al proyecto backend

bash

Copiar código

cd prueba-tecnica/backend

Compilar el proyecto

bash

Copiar código

mvn clean install

Ejecutar la aplicación

bash

Copiar código

mvn spring-boot:run

📍 El backend quedará disponible en:

arduino

Copiar código

http://localhost:8080

⚙️ Configuración del Backend

Archivo: application.properties

properties

Copiar código

spring.datasource.url=jdbc:mysql://localhost:3306/pruebatecnica

spring.datasource.username=root

spring.datasource.password=root

spring.jpa.hibernate.ddl-auto=update

spring.jpa.show-sql=true

jwt.secret=miClaveSecretaSuperSeguraParaJWT2024DebeSerLargaYCompleja

jwt.expiration=86400000

▶️ Ejecución del Frontend

Requisitos

Node.js 18 o superior

npm o yarn

Pasos

Clonar el repositorio del frontend

bash

Copiar código

git clone https://github.com/NSMG27/pruebatecnica-usco-front.git

Entrar al proyecto frontend

bash

Copiar código

cd frontend

Instalar dependencias

bash

Copiar código

npm install

Ejecutar la aplicación

bash

Copiar código

npm run dev

📍 El frontend quedará disponible en:

arduino

Copiar código

http://localhost:4200

🌐 Configuración del Frontend

Archivo .env

env

Copiar código

VITE\_API\_URL=http://localhost:8080/api

🗄️ Estructura de la Base de Datos

Tabla: user

iduser (PK)

name

email

password

role (ENUM)

Tabla: type\_of\_procedure

idtype\_of\_procedure (PK)

name

Tabla: procedure

idthrough (PK)

user\_iduser (FK)

type\_of\_procedure\_id (FK)

description

state (ENUM)

creationdate

Tabla: document\_type

iddocument\_type (PK)

name

Tabla: type\_of\_procedure\_has\_document\_type

type\_of\_procedure\_id (PK, FK)

document\_type\_id (PK, FK)

Tabla: attachment

idattachment (PK)

procedure\_id (FK)

document\_type\_id (FK)

url

Tabla: tracing

idtracing (PK)

through\_idthrough (FK)

user\_iduser (FK)

comment

creationdate

🔗 Endpoints principales

Autenticación

POST /api/auth/register

POST /api/auth/login

Trámites

POST /api/tramites

GET /api/tramites

PATCH /api/tramites/{id}/assign

PATCH /api/tramites/{id}/state

Documentos requeridos

GET /api/tramites/tipos/{id}/documentos

POST /api/tramites/tipos/{id}/documentos

Seguimiento del trámite

POST /api/tramites/{id}/seguimiento

GET /api/tramites/{id}/seguimiento

🔐 Autenticación JWT

Realizar login

Obtener token JWT

Enviar el token en cada request:

http

Copiar código

Authorization: Bearer <TOKEN>

👤 Credenciales de prueba

Usuario Estudiante

Email: student@test.com

Password: 1234

Rol: STUDENT

Usuario Funcionario

Email: teacher@test.com

Password: 1234

Rol: TEACHER

🧠 Decisiones de arquitectura

Uso de Domain Driven Design (DDD)

Separación clara de capas: dominio, aplicación e infraestructura

Reglas de negocio encapsuladas en casos de uso

Seguridad stateless basada en JWT

Normalización de relaciones N–N

Controladores sin lógica de negocio

✍️ Autor

Nicolás Mosquera

📧 Correo: nicolas.mosquerago@outlook.com

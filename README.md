# PRUEBA TÉCNICA – SISTEMA DE GESTIÓN DE TRÁMITES

## 📌 Descripción general

Sistema web para la **gestión y seguimiento de trámites**, desarrollado como prueba técnica. La solución está compuesta por un **backend en Spring Boot**, siguiendo principios de **Domain Driven Design (DDD)**, y un **frontend moderno desacoplado**, con autenticación **JWT stateless**.

---

## 🧱 Stack tecnológico

### Backend

- **Java 17**
- **Spring Boot**
- **Spring Security** (JWT)
- **Spring Data JPA / Hibernate**
- **Arquitectura DDD**
- **Base de datos**: MySQL 8 (H2 opcional para pruebas)

### Frontend

- **Node.js 18+**
- Framework frontend moderno
- Consumo de API REST

---

## ▶️ Ejecución del Backend

### Requisitos

- Java 17 o superior  
- Maven 3.8 o superior  
- MySQL 8 (opcional H2)  
- Git  

### Pasos

1. Clonar el repositorio

```bash
git clone https://github.com/NSMG27/pruebatecnica-usco.git
```

2. Entrar al proyecto backend

```bash
cd prueba-tecnica/backend
```

3. Compilar el proyecto

```bash
mvn clean install
```

4. Ejecutar la aplicación

```bash
mvn spring-boot:run
```

📍 El backend quedará disponible en:

```
http://localhost:8080
```

---

## ⚙️ Configuración del Backend

Archivo: `application.properties`

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/pruebatecnica
spring.datasource.username=root
spring.datasource.password=root

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

jwt.secret=miClaveSecretaSuperSeguraParaJWT2024DebeSerLargaYCompleja
jwt.expiration=86400000
```

---

## ▶️ Ejecución del Frontend

### Requisitos

- Node.js 18 o superior  
- npm o yarn  

### Pasos

1. Clonar el repositorio del frontend

```bash
git clone https://github.com/NSMG27/pruebatecnica-usco-front.git
```

2. Entrar al proyecto frontend

```bash
cd frontend
```

3. Instalar dependencias

```bash
npm install
```

4. Ejecutar la aplicación

```bash
npm run dev
```

📍 El frontend quedará disponible en:

```
http://localhost:4200
```

---

## 🌐 Configuración del Frontend

Archivo `.env`

```env
VITE_API_URL=http://localhost:8080/api
```

---

## 🗄️ Estructura de la Base de Datos

### Tabla: `user`

- iduser (PK)
- name
- email
- password
- role (ENUM)

### Tabla: `type_of_procedure`

- idtype_of_procedure (PK)
- name

### Tabla: `procedure`

- idthrough (PK)
- user_iduser (FK)
- type_of_procedure_id (FK)
- description
- state (ENUM)
- creationdate

### Tabla: `document_type`

- iddocument_type (PK)
- name

### Tabla: `type_of_procedure_has_document_type`

- type_of_procedure_id (PK, FK)
- document_type_id (PK, FK)

### Tabla: `attachment`

- idattachment (PK)
- procedure_id (FK)
- document_type_id (FK)
- url

### Tabla: `tracing`

- idtracing (PK)
- through_idthrough (FK)
- user_iduser (FK)
- comment
- creationdate

---

## 🔗 Endpoints principales

### Autenticación

- `POST /api/auth/register`
- `POST /api/auth/login`

### Trámites

- `POST /api/tramites`
- `GET /api/tramites`
- `PATCH /api/tramites/{id}/assign`
- `PATCH /api/tramites/{id}/state`

### Documentos requeridos

- `GET /api/tramites/tipos/{id}/documentos`
- `POST /api/tramites/tipos/{id}/documentos`

### Seguimiento del trámite

- `POST /api/tramites/{id}/seguimiento`
- `GET /api/tramites/{id}/seguimiento`

---

## 🔐 Autenticación JWT

1. Realizar login  
2. Obtener token JWT  
3. Enviar el token en cada request:

```http
Authorization: Bearer <TOKEN>
```

---

## 👤 Credenciales de prueba

### Usuario Estudiante

- Email: `student@test.com`
- Password: `1234`
- Rol: `STUDENT`

### Usuario Funcionario

- Email: `teacher@test.com`
- Password: `1234`
- Rol: `TEACHER`

---

## 🧠 Decisiones de arquitectura

- Uso de **Domain Driven Design (DDD)**
- Separación clara de capas: dominio, aplicación e infraestructura
- Reglas de negocio encapsuladas en casos de uso
- Seguridad stateless basada en JWT
- Normalización de relaciones N–N
- Controladores sin lógica de negocio

---

## ✍️ Autor

**Nicolás Mosquera**  
📧 Correo: [nicolas.mosquerago@outlook.com](mailto:nicolas.mosquerago@outlook.com)

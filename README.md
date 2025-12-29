# 🧩 Arquitectura de Microservicios con Spring Boot  
### Proyecto Backend Profesional — CRUD, JPA Avanzado, Swagger, Testing, CI/CD, Docker, RabbitMQ

Este proyecto implementa una arquitectura completa de **microservicios** usando Spring Boot, con un enfoque profesional orientado a producción.  
Incluye CRUDs completos, persistencia avanzada, documentación automática, pruebas unitarias e integración, mensajería asíncrona y pipeline CI/CD con Docker.

---

## 🏗️ Arquitectura General

El sistema está dividido en varios microservicios independientes:

- **User Service**
- **Product Service**
- **Order Service**

Cada microservicio:
- Tiene su propio modelo, repositorio, servicio y controlador.
- Expone su API REST documentada con OpenAPI.
- Se ejecuta en un puerto independiente.
- Se comunica vía REST y mensajería.

---

## 📦 Tecnologías principales

| Categoría | Tecnologías |
|----------|-------------|
| Backend | Spring Boot 3, Spring Web, Spring Validation |
| Persistencia | Spring Data JPA, Hibernate, H2/MySQL/PostgreSQL |
| Migraciones | Flyway |
| Documentación | springdoc-openapi, Swagger UI |
| Testing | JUnit 5, Mockito, MockMvc, DataJpaTest |
| Mensajería | RabbitMQ (Publisher/Consumer) |
| Contenedores | Docker, Docker Compose |
| CI/CD | GitHub Actions / GitLab CI |

---

## 🗄️ Persistencia Avanzada

El proyecto incluye:

- Entidades relacionadas (`Order`, `Product`, `User`)
- Relaciones JPA:
  - `@OneToMany`
  - `@ManyToOne`
- Consultas personalizadas:
  - Query Methods
  - `@Query` con JPQL
- Migraciones versionadas:
  - `V1__init.sql`

---

## 📘 Documentación OpenAPI

El proyecto integra **springdoc-openapi**:

- Documentación automática en  
  **`/swagger-ui.html`**  
- Esquemas enriquecidos con:
  - `@Schema(description = "...")`
  - `@Schema(example = "...")`
  - `@Operation(summary = "...")`

---

## 🧪 Testing

### ✔ Pruebas unitarias
- Servicios probados con Mockito (`@Mock`, `@InjectMocks`)
- Repositorios probados con DataJpaTest

### ✔ Pruebas de integración
- Controladores probados con `@SpringBootTest` + `MockMvc`
- Validación de endpoints, JSON y códigos HTTP

### ✔ Cobertura
- Configuración mínima en SonarQube
- Análisis sin fallos críticos ni blockers

---

## 🐳 Docker & CI/CD

### ✔ Dockerfile
- Imagen ligera y optimizada
- Multi-stage build (si aplica)

### ✔ docker-compose
Incluye:
- Microservicios
- Base de datos
- RabbitMQ

### ✔ Pipeline CI/CD
- Build automático
- Ejecución de tests
- Publicación de imagen en Docker Hub
- 
---

## 📡 Mensajería Asíncrona (RabbitMQ)

El sistema implementa un flujo real de eventos:

1. El microservicio **Order** crea un pedido.
2. Publica un mensaje en RabbitMQ.
3. Los microservicios **Product y User** consumen el mensaje.
4. Procesa la notificación (log, email simulado, etc.).

Tecnologías:
- `RabbitTemplate`
- `@RabbitListener`
- Exchanges, Queues y Bindings configurados

---

## 🧭 Endpoints principales


Cada microservicio expone endpoints REST como:

GET /api/users
POST /api/users
DELETE /api/users/{id}

GET /api/products
POST /api/products

GET /api/orders
POST /api/orders


Todos documentados en Swagger.

---

## 🧱 Estructura del repositorio

/common-dto
/eurekaServer
/user-service
/product-service
/order-service
/init-db
/docker-compose.yml


---

## 🚀 Cómo ejecutar el proyecto

### Opción 1: Docker Compose
```bash
docker compose up --build

### Opción 2: Manual
Ejecutar cada microservicio con:

mvn spring-boot:run

## 🙌 Créditos y agradecimientos

Este proyecto comenzó como una base inspirada en un tutorial de YouTube, pero ha sido ampliado y refactorizado en profundidad para incluir arquitectura de microservicios, mensajería con RabbitMQ, CI/CD, testing avanzado, documentación OpenAPI y despliegue con Docker Compose.

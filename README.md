# Restaurant Management API · Spring Boot

REST API for managing restaurants, menus, employees, customers and orders, with JWT authentication and role-based access. Built as a university team project following an agile workflow with user stories (HU), feature branches and pull requests.

> **Team project.** Developed with [@lopezu59](https://github.com/lopezu59), [@emma5mau](https://github.com/emma5mau) and Santiago Esparza. Original repository: [proyectoorganizacion/Restaurante_springboot](https://github.com/proyectoorganizacion/Restaurante_springboot).

## Tech stack

- **Java 25** · **Spring Boot 4**
- Spring Web MVC · Spring Data JPA (Hibernate) · Spring Security
- **JWT** authentication (jjwt) with BCrypt password hashing
- **MySQL**
- Bean Validation · Lombok · Maven
- Postman for API testing · Mermaid for diagrams

## Architecture

Layered architecture:

```
controller  →  service (interfaces + impl)  →  repository  →  MySQL
     ↑                    ↑
   DTOs (request / response)     entity (JPA)
security (JWT filter, config) · handler (global exceptions)
```

Class and data diagrams are in [`Diagrama de clases de restaurante.mmd`](./Diagrama%20de%20clases%20de%20restaurante.mmd) and [`Diagrama de datos Restaurante.mmd`](./Diagrama%20de%20datos%20Restaurante.mmd).

## Features

| Area | Endpoints |
| --- | --- |
| Auth | `POST /api/v1/auth/login` · `POST /api/v1/auth/crear-admin` |
| Users | `POST /api/v1/usuarios/registro` · `/empleado` · `/cliente` |
| Restaurants | `POST /restaurante` · `GET /restaurante/listar` (paginated) |
| Dishes | `POST /api/v1/platos/registro` · `PUT /api/v1/platos/{id}` · `PUT /api/v1/platos/{id}/estado` · `GET /api/v1/platos/restaurante/{id}` |
| Categories | `POST /api/v1/categorias/registro` · `GET /api/v1/categorias` |
| Orders | `POST /api/v1/pedidos` · `GET /api/v1/pedidos` (pending, paginated) |

Roles: administrator, restaurant owner, employee and customer, each with its own permissions.

## My contributions

- **Database design:** designed and evolved the MySQL schema (`restaurante_db.sql`) and the data model.
- **HU-9 · List restaurants (paginated):** controller, service, repository and response DTO.
- **HU-10 · List dishes by restaurant:** filtered and paginated query of a restaurant's menu.
- **HU-11 · Place an order:** order and order-detail entities, DTOs, validation and business logic in `PedidoServiceImpl`.
- **Diagrams:** class diagram and data diagram in Mermaid.
- **Code review:** reviewed and merged team pull requests.

## Run locally

Requirements: Java 25, MySQL 8.

```bash
git clone https://github.com/julian11gm/Restaurante_springboot.git
cd Restaurante_springboot

# 1. Create the database
mysql -u root -p < restaurante_db.sql

# 2. Set your DB credentials and JWT secret in src/main/resources/application.properties

# 3. Run
./mvnw spring-boot:run
```

The API runs on `http://localhost:8080`. Import the Postman collection from `src/main/java/com/restaurante/restaurante_spring/postman/` to try every endpoint.

---

### Español

API REST para gestionar restaurantes, platos, empleados, clientes y pedidos, con autenticación JWT y roles. Proyecto universitario en equipo, trabajado con historias de usuario, ramas por funcionalidad y pull requests. Mis aportes: diseño de la base de datos, HU-9 (listar restaurantes paginados), HU-10 (listar platos por restaurante), HU-11 (realizar pedido) y los diagramas de clases y de datos.

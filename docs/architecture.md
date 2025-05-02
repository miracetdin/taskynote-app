# TaskyNote - Architecture

## Overview

TaskyNote is a personal note and task management application designed with a layered architecture approach. It adheres to best practices for modularity, separation of concerns, and scalability. The project is developed using Java 21 and Spring Boot.

```
[HTTP Request]
↓
[Controller Layer]
↓
[Service Layer]
↓
[Repository Layer]
↓
[Database]
```

### 1. Controller Layer

- Responsible for handling HTTP requests and routing them to appropriate services.
- Does not contain any business logic.
- Accepts and returns DTOs for clean API boundaries.
- Annotated with `@RestController`.

### 2. Service Layer

- Contains business logic and domain-specific operations.
- Interacts with repositories and other services.
- Handles validations, filtering, sorting, and cross-entity operations.
- Annotated with `@Service`.

### 3. Repository Layer

- Handles data persistence logic.
- Uses Spring Data JPA interfaces such as "JpaRepository".
- Abstracts away database queries from business logic.
- Annotated with `@Repository`.

### 4. Entity Layer

- Represents the database schema as Java classes.
- Each entity maps to a table.
- Entity relationships are modeled using JPA annotations such as `@OneToMany`.
- Annotated with `@Entity`.

---

## Flow Example - Creating a New Task

1. `POST api/tasks` is called with JSON body.
2. `TaskController.createTask()` receives the request.
3. DTO is passed to `TaskService`.
4. `TaskService`:
   1. Validates task logic,
   2. Checks dependency rules,
   3. Converts DTO to entity,
   4. Saves to DB via `TaskRepository`.
5. Returns a response DTO with task info.

---

## Package Structure

```
com.taskynote
├── config          # Application-wide configurations
├── controller      # REST API controllers
├── dto             # Request and Response DTOs
├── exception       # Custom exceptions and handlers
├── model           # JPA entities
├── repository      # Spring Data repositories
├── services        # Business logic
├── util            # Utility classes
└── TaskyNoteApplication.java
```

---

## Entity Relationship

- `User` has many `Notes` and `Tasks`.
- `Task` can be related to one or more `Notes`.
- `Task` can depend on other `Tasks` (optional).
- `Tag` is user-specific and can be attached to `Note` or `Task`.

(See `docs/entity-relationship.md` and `docs/entity-relationship.puml` for the complete ER diagram.)

---

## Technology Stack

- **Backend:** Java 21, Spring Boot 3.4.x
- **Database:** PostgreSQL
- **ORM:** Spring Data JPA, Hibernate
- **Security:** JWT-based auth via Spring Security
- **Build Tool:** Maven
- **Documentation:** Markdown + PlantUML

---

## Future Enhancements

- Add caching layer (e.g., Redis, Hazelcast).
- Implement async task execution.
- Introduce message queue for notifications.
- Switch to modular monolith or microservices for scalability.

---

## Notes

- Business rules like "dependent tasks must be completed in order" are enforced in the service layer.
- Tag visibility and CRUD operations are scoped per user.
- DTOs are mapped manually or using MapStruct.

--- 

## DTO-Entity Mapping Strategy

Data Transfer Objects (DTOs) are used at the API boundaries to isolate internal entity models from external consumers. DTO-to-entity and entity-to-DTO mappings are handled manually within the service layer. 

---

## Transaction Management

Transactional boundaries are defined at the service layer using Spring's `@Transactional` annotation. This ensures that multiple related database operations within a business use-case are either all committed or rolled back, maintaining consistency.

---

## Exception Handling

Global exception handling is implemented using `@ControllerAdvice` and `@ExceptionHandler`. This allows TaskyNote to catch and respond to errors in a consistent, structured format (e.g., HTTP 400/404/500 with JSON error payloads) while keeping the controller layer clean.

---

## Validation Strategy

Field-level validation is applied on DTO classes using Jakarta Bean Validation annotations such as `@NotNull`, `@Size` and `@Pattern`. The controller methods use the `@Valid` annotation to trigger these validations automatically before processing any input.

---

## Authorization Strategy

Resource-level access control is enforced in the service layer. All domain entities are user-scoped, meaning a user can only create, read, update, or delete their own notes, tasks, and tags. Identity checks are applied before performing any domain operation.

---

## Business Rules

- A task can only be marked as completed if all of its dependencies (preceding tasks) are also completed.
- Tasks with dependencies must be executed in order. The application prevents skipping dependent tasks.
- Tags are user-specific and cannot be shared across users.
- Notes can be linked to multiple tasks, and tasks can reference multiple notes.
- Deleted tags should be automatically disassociated from all related tasks and notes.

---

## Modular Packaging

Currently, the project follows a layered package structure (controller, service, repository). However, as the application grows, the structure may shift toward a domain-driven modular layout such as:

```
com.taskynote.task
├── TaskController.java
├── TaskService.java
├── TaskRepository.java
└── Task.java
```

This allows better cohesion and reduces naming collisions for large-scale feature sets.

---

## API Specification Reference

All endpoint definitions, including paths, HTTP Methods, input/output schemas, and status codes, are maintained separately in the file: `docs/api-specifications.md`. 

Refer to this file for detailed API contract definitions when implementing or consuming endpoints.

---

## Configuration Management

The application uses environment-specific configuration files (`application-dev.yml`, `application-prod.yml`) to separate settings across development and production environments. These configurations include database URLs, JWT secrets, logging levels, and external service credentials.

---

## Testing Strategy

The project will adopt the following testing approach:
- **Unit Tests:** Target the service layer with isolated business logic using *JUnit* 5 and *Mockito*.
- **Integration Tests:** Use `@SpringBootTest` and *MockMvc* to verify controller-to-database flow for key use-cases.
- **Repository Tests:** Use `@DataJpaTest` to validate JPA query behavior and data integrity.

Test coverage will prioritize business logic and edge cases related to task ordering and note-task relationships.
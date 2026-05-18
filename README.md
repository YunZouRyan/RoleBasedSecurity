# RoleBasedSecurity

A Java-based REST API for a task management system featuring JWT (JSON Web Token) authentication and role-based authorization. Users can register, log in, and manage their own tasks, while admin users have access to additional endpoints for viewing all registered users.

## Features
- Stateless JWT-based authentication
- User registration and login with BCrypt password hashing
- Role-based access control (USER and ADMIN roles)
- Per-user task management (create, read, update, delete)
- Tasks are scoped to the authenticated user — users can only access their own data
- Admin-only endpoint to list all registered users

## Requirements
- Java 17
- Maven

## Technologies
- **Language:** Java 17
- **Framework:** Spring Boot 3.4.4
- **Security:** Spring Security, JWT (jjwt 0.12.6), BCrypt password encoding, custom JWT filter chain
- **Persistence:** Spring Data JPA, Hibernate, H2 (embedded), MySQL (optional)
- **Web:** Spring Web REST (`@RestController`)
- **Build Tool:** Maven
- **Dev Tools:** Spring Boot DevTools (hot reload)
- **Other:** Lombok (`@Data`, `@Builder`, `@AllArgsConstructor`, `@NoArgsConstructor`, `@RequiredArgsConstructor`)

## API Endpoints

### Authentication (public)
| Method | Endpoint              | Description                          |
|--------|-----------------------|--------------------------------------|
| POST   | `/api/auth/register`  | Register a new user, returns JWT     |
| POST   | `/api/auth/login`     | Authenticate, returns JWT            |

### Tasks (USER or ADMIN)
| Method | Endpoint              | Description                          |
|--------|-----------------------|--------------------------------------|
| GET    | `/api/tasks`          | Get all tasks for the current user   |
| POST   | `/api/tasks`          | Create a new task                    |
| PUT    | `/api/tasks/{id}`     | Update an existing task              |
| DELETE | `/api/tasks/{id}`     | Delete a task                        |

### Admin (ADMIN only)
| Method | Endpoint              | Description                          |
|--------|-----------------------|--------------------------------------|
| GET    | `/api/admin/users`    | List all registered users            |

Authenticated endpoints require an `Authorization: Bearer <token>` header.

## Getting Started
Clone the repository and run the application:

```bash
mvn spring-boot:run
```

Once started, the API is available at `http://localhost:8080/`.

The H2 console is available at `http://localhost:8080/h2-console/`.

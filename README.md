# Task Manager API

Spring Boot REST API for managing tasks. The application exposes CRUD endpoints, stores data with Spring Data JPA, and uses an in-memory H2 database for local development and testing.

## Technologies

- Java 25
- Spring Boot 4
- Spring Web
- Spring Data JPA
- H2 Database
- Maven

## Project Structure

```text
src/
├── main/
│   ├── java/gl2/example/taskmanager/
│   │   ├── TaskApplication.java
│   │   ├── controller/TaskController.java
│   │   ├── model/Task.java
│   │   ├── repository/TaskRepository.java
│   │   └── service/TaskService.java
│   └── resources/
│       ├── application.properties
│       ├── static/
│       └── templates/
└── test/java/gl2/example/taskmanager/
    └── TaskApplicationTests.java
```

## Running the Project

From the project root:

```powershell
.\mvnw.cmd spring-boot:run
```

The API starts at:

```text
http://localhost:8080
```

Run tests with:

```powershell
.\mvnw.cmd test
```

## H2 Database

The project uses an in-memory H2 database. Data is reset every time the application restarts.

H2 console:

```text
http://localhost:8080/h2-console
```

Connection settings:

```text
JDBC URL: jdbc:h2:mem:taskdb
Username: sa
Password:
```

## Task Model

```json
{
  "id": 1,
  "title": "Complete Spring Boot Project",
  "description": "Finish the Task Management API and test with Postman.",
  "completed": false
}
```

## Endpoints

| Method | Endpoint | Description |
| --- | --- | --- |
| `POST` | `/api/tasks` | Create a new task |
| `GET` | `/api/tasks` | Get all tasks |
| `GET` | `/api/tasks/{id}` | Get one task by ID |
| `PUT` | `/api/tasks/{id}` | Update an existing task |
| `DELETE` | `/api/tasks/{id}` | Delete a task |

## Request Examples

### Create Task

```http
POST /api/tasks
Content-Type: application/json
```

```json
{
  "title": "Complete Spring Boot Project",
  "description": "Finish the Task Management API and test with Postman.",
  "completed": false
}
```

Expected status: `201 Created`

### Get All Tasks

```http
GET /api/tasks
```

Expected status: `200 OK`

### Get Task by ID

```http
GET /api/tasks/1
```

Expected status: `200 OK` if the task exists, or `404 Not Found` if it does not.

### Update Task

```http
PUT /api/tasks/1
Content-Type: application/json
```

```json
{
  "title": "Complete Spring Boot Project",
  "description": "Everything is working correctly!",
  "completed": true
}
```

Expected status: `200 OK` if the task exists, or `404 Not Found` if it does not.

### Delete Task

```http
DELETE /api/tasks/1
```

Expected status: `204 No Content` if the task exists, or `404 Not Found` if it does not.

## Postman

A Postman collection is included at:

```text
postman/Task Management API.postman_collection.json
```

Import it into Postman, start the application, then run the requests in this order:

1. Create Task
2. Get All Tasks
3. Get Task by ID
4. Update Task
5. Delete Task

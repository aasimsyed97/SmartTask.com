# SmartTask.com
A task management system (like Trello or Jira-lite)
where:  Users can create projects  
Assign tasks to teammates  
Set due dates, priority, and status
Use filters/search  
Admins can manage users, roles, and team structure


💡 Project Overview
A task management system (like Trello or Jira-lite) where:

Users can create projects

Assign tasks to teammates

Set due dates, priority, and status

Use filters/search

Admins can manage users, roles, and team structure

🏗️ Tech Stack
🖥️ Backend:
Java 17

Spring Boot (REST APIs)

Spring Security (JWT-based auth)

Spring Data JPA + PostgreSQL

MongoDB (for activity logs or task comments)

Liquibase (DB versioning)

Microservices (Auth, Task, Notification)

Redis (caching task metadata)

🧪 DevOps:
Dockerize each service

Docker Compose to run full stack

CI/CD with GitHub Actions or Jenkins

Use Swagger or Postman for API docs

🔄 Bonus Features (Optional but impressive)
Email notifications (on task assignment or updates)

Audit logs using MongoDB

RabbitMQ/Kafka to decouple notification service

Rate limiting with Bucket4j or Resilience4j

📦 Deliverables
Code on GitHub (structured well, README with setup guide)

Optional: Deploy backend to Render, Railway, or AWS EC2

API documentation with Swagger UI

Add Postman collection for demo/testing




SmartTask (Backend)
│
├── auth-service (Spring Boot + Spring Security + JWT)
│     └── Users, Roles, Login/Signup, Token management
│
├── task-service (Spring Boot)
│     └── Projects, Tasks, Assignees, Status, CRUD
│
├── notification-service (Spring Boot)
│     └── Email (Optional: Kafka-based async handling)
│
├── activity-service (Spring Boot + MongoDB)
│     └── Logs of task updates, user actions (read-only)
│
│
├── shared-libs (Common DTOs, Exception Handling)
│
└── docker-compose.yml


Project Root Structure:
smarttask/
├── auth-service/
├── user-service/
├── task-service/
├── project-service/
├── notification-service/
├── activity-service/
├── docker-compose.yml
├── README.md
└── .gitignore

Inside Each service we will follow following structure: 

service-name/
├── src/
│   ├── main/
│   │   ├── java/com/smarttask/servicename/
│   │   │   ├── config/
│   │   │   ├── controller/
│   │   │   ├── dto/
│   │   │   ├── entity/
│   │   │   ├── exception/
│   │   │   ├── repository/
│   │   │   ├── service/
│   │   │   └── SmartTask[ServiceName]Application.java
│   │   └── resources/
│   │       ├── application.yml
│   │       └── db/
│   │           └── changelog/
│   │               └── db.changelog-master.xml (if using Liquibase)
│   └── test/
│       └── java/com/smarttask/servicename/
│           └── [Unit + Integration tests]
├── Dockerfile
├── pom.xml
└── README.md



✅ 1. Folder Structure Update (with common-libs)
pgsql
Copy
Edit
smarttask/
├── common-libs/              <-- Shared DTOs, enums, exceptions
│   ├── src/main/java/com/smarttask/common/
│   │   ├── dto/
│   │   ├── enums/
│   │   └── exception/
│   └── pom.xml
├── auth-service/
├── user-service/
├── task-service/
├── project-service/
├── notification-service/
├── activity-service/
├── docker-compose.yml
├── README.md
└── .gitignore
Each service’s pom.xml will import common-libs as a dependency.

📦 2. common-libs Contents
dto/

UserDTO.java

AuthRequest.java

AuthResponse.java

TaskDTO.java

enums/

UserRole.java

TaskStatus.java

exception/

ApiException.java

GlobalExceptionHandler.java

ErrorResponse.java




📌 Swagger Endpoints (via Springdoc OpenAPI)
Method	Endpoint	Description
POST	/api/auth/register	Register a new user
POST	/api/auth/login	Login & get JWT
GET	/api/auth/me	Get current user info
POST	/api/auth/validate	(Internal) validate token
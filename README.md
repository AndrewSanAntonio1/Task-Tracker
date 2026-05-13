# Task Tracker Web App (Senior Dev Roadmap)

You will build:

```text
Frontend (HTML/CSS/JS)
        ↓ fetch()
Spring Boot REST API
        ↓
tasks.json
```

Goal:

* Learn CRUD
* Learn REST APIs
* Learn file handling
* Learn frontend-backend connection

---

# STACK

Frontend:

* HTML
* CSS
* Vanilla JS

Backend:

* Java
* Spring Boot
* Jackson JSON

Storage:

* JSON file

Build Tool:

* Gradle or Maven

---

# PHASE 1 — CREATE BACKEND

## 1. Generate Spring Boot Project

Use:

* Spring Web

Project name:

```text
task-tracker-backend
```

Package:

```text
com.tasktracker
```

---

# 2. Project Structure

```text
src/main/java/com/tasktracker/

├── controller/
├── service/
├── model/
├── util/
└── TaskTrackerApplication.java
```

---

# 3. Create Task Model

File:

```text
model/Task.java
```

Fields:

```java
private int id;
private String description;
private String status;
private String createdAt;
private String updatedAt;
```

Generate:

* getters
* setters
* constructors

Status values:

* todo
* in-progress
* done

---

# 4. Create JSON File

Root folder:

```text
tasks.json
```

Initial content:

```json
[]
```

---

# 5. Create TaskService

File:

```text
service/TaskService.java
```

Responsibilities:

* read tasks.json
* write tasks.json
* CRUD logic

---

# 6. Setup Jackson

Use:

```java
ObjectMapper
```

Functions:

```java
loadTasks()
saveTasks()
```

---

# 7. Implement CRUD

## ADD TASK

Method:

```java
addTask(String description)
```

Flow:

1. Read JSON
2. Generate ID
3. Create task
4. status = "todo"
5. createdAt = now
6. updatedAt = now
7. Save JSON

---

## GET TASKS

Method:

```java
getAllTasks()
```

Return list.

---

## UPDATE TASK

Method:

```java
updateTask(int id, String description)
```

Flow:

1. Find task
2. Update description
3. Update updatedAt
4. Save

---

## DELETE TASK

Method:

```java
deleteTask(int id)
```

---

## MARK STATUS

Method:

```java
updateStatus(int id, String status)
```

Allowed:

* todo
* in-progress
* done

---

## FILTER BY STATUS

Method:

```java
getTasksByStatus(String status)
```

---

# PHASE 2 — CREATE CONTROLLER

File:

```text
controller/TaskController.java
```

Use:

```java
@RestController
@RequestMapping("/tasks")
@CrossOrigin("*")
```

---

# API DESIGN

---

## CREATE TASK

```http
POST /tasks
```

Body:

```json
{
  "description": "Buy groceries"
}
```

---

## GET ALL TASKS

```http
GET /tasks
```

---

## GET TASKS BY STATUS

```http
GET /tasks/status/done
```

---

## UPDATE TASK

```http
PUT /tasks/1
```

Body:

```json
{
  "description": "New task"
}
```

---

## DELETE TASK

```http
DELETE /tasks/1
```

---

## UPDATE STATUS

```http
PATCH /tasks/1/status
```

Body:

```json
{
  "status": "done"
}
```

---

# PHASE 3 — TEST BACKEND

Use:

* Postman
  OR
* browser
  OR
* Thunder Client VSCode extension

Test ALL endpoints before frontend.

---

# PHASE 4 — CREATE FRONTEND

Structure:

```text
frontend/

├── index.html
├── style.css
└── script.js
```

---

# HTML

Create:

* input
* add button
* filter buttons
* task list container

Example:

```html
<input id="taskInput">
<button>Add</button>

<div id="taskList"></div>
```

---

# CSS

Keep simple:

* flexbox
* spacing
* card design
* status colors

---

# JAVASCRIPT

Core functions:

```javascript
loadTasks()
addTask()
deleteTask()
updateTask()
markDone()
markInProgress()
filterTasks()
```

---

# FETCH API

Example:

```javascript
fetch("http://localhost:8080/tasks")
```

---

# LOAD TASKS

Flow:

1. fetch GET /tasks
2. loop tasks
3. render HTML

---

# ADD TASK

Flow:

1. get input value
2. POST /tasks
3. reload tasks

---

# DELETE TASK

Flow:

1. DELETE /tasks/id
2. reload tasks

---

# UPDATE STATUS

Flow:

1. PATCH /tasks/id/status
2. send status
3. reload tasks

---

# RENDER TASK CARD

Each task should show:

* description
* status
* created date
* buttons

Example buttons:

* Edit
* Delete
* Done
* In Progress

---

# PHASE 5 — ERROR HANDLING

Backend:

* invalid ID
* empty description
* invalid status
* corrupted JSON

Frontend:

* empty input
* failed requests

---

# PHASE 6 — CLEAN ARCHITECTURE

DO NOT:

* put all logic in controller
* manipulate JSON in controller

DO:

* controller → handles HTTP
* service → business logic
* model → data structure

---

# PHASE 7 — FINAL FEATURES

Minimum:

* add
* update
* delete
* list
* filter
* mark done
* mark in progress

---

# OPTIONAL SENIOR FEATURES

After MVP works:

## GOOD ADDITIONS

* search
* pagination
* dark mode
* localStorage caching
* animations
* Docker
* MySQL
* JWT auth
* React frontend
* deploy backend

---

# RECOMMENDED DEVELOPMENT ORDER

1. Task model
2. JSON read/write
3. Add task
4. Get tasks
5. Update task
6. Delete task
7. Status update
8. Test backend
9. Build frontend
10. Connect frontend


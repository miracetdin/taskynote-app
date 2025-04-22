# TaskyNote - Requirements Document

## 1. Introduction
TaskyNote is a personal application that allows users to manage their notes and tasks. The application supports defining dependency relationships between tasks, associating tasks with notes, and organizing content through user-specific tagging.

## 2. Definitions
- **Note**: A textual information record created by the user.
- **Task**: A to-do item that needs to be completed.
- **Tag**: A user-defined keyword used to categorize notes or tasks.

## 3. Functional Requirements

### 3.1. Note Management
- Users should be able to create notes.
- Users should be able to list notes.
- Users should be able to update notes.
- Users should be able to delete notes.
- Notes should be taggable.

### 3.2. Task Management
- Users should be able to create tasks.
- Users should be able to list tasks.
- Users should be able to update tasks.
- Users should be able to delete tasks.
- Tasks should be taggable.
- Tasks should be definable in a sequential/dependent order.
- A task that is dependent on another cannot be started until the previous task is completed.

### 3.3. Note-Task Relationship
- Users should be able to associate one or more notes with a task.
- From a note, related task(s) should be viewable.

### 3.4. Tag Management
- Tags should be user-specific.
- Users should be able to create tags.
- Users should be able to list tags.
- Users should be able to delete tags.
- Users should be able to filter notes and tasks by tags.

### 3.5 User Management
- Users should be able to register.
- Users should be able to log in.
- Each user's data should be private and only visible to them.

## 4. Non-Functional Requirements
- The application should follow a RESTful API architecture.
- PostgreSQL or MongoDB should be used as the database.
- The backend should be developed using Java Spring Boot.
- The frontend should be developed using .NET, HTML, CSS, and JavaScript.
- The application should be containerized using Docker.
- Git should be used for version control and managed via GitHub.

## 5. Constraints
- The user interface will be kept simple for the initial version.

## 6. Future Enhancements
- Email-based reminder notifications.
- Task completion analytics.
- Relationships between tags (hierarchical tagging system).
- Mobile application support.

---
*Last updated: April 22, 2025*
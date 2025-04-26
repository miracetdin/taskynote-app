# TaskyNote - Use Cases

## 1. User Registration
- **Description:** New users can create an account.
- **Basic Flow:** 
  1. Users enter email, username and password.
  2. System validates and saves users.

## 2. User Login
- **Description:** Registered users can log into their account.
- **Basic Flow:**
 1. User provides email/username and password.
 2. System authenticates user and grants access.

## 3. Create Note
- **Description:** Users can create a new note.
- **Basic Flow:**
  1. Users clicks "Create Note".
  2. Users enters note title and content.
  3. Users assigns tags (optional).
  4. System saves the note.

## 4. View Note
- **Description:** Users can view a note.
- **Basic Flow:**
  1. User clicks a note.
  2. System displays note details.

## 5. View Notes
- **Description:** Users can view a list of their notes.
- **Basic Flow:**
  1. User navigates to "My Notes".
  2. User selects some filters like that tags, due date etc. (optional).
  3. System displays a list of notes.

## 6. Edit Note
- **Description:** Users can edit an existing note.
- **Basic Flow:**
  1. User selects a note.
  2. User modifies title/content/tags and links.
  3. System saves changes.

## 7. Delete Note
- **Description:** Users can delete a note.
- **Basic Flow:**
  1. User selects a note.
  2. User confirms deletion.
  3. System removes the note.
   
## 8. Create Task
- **Description:** Users can create a new task.
- **Basic Flow:**
  1. User clicks "Create Task".
  2. User enters task title, description, and due date.
  3. User links notes (optional).
  4. User sets dependency to another task (optional).
  5. System saves the task.

## 9. View Task
- **Description:** Users can view a task.
- **Basic Flow:**
  1. User clicks a task.
  2. System displays task details.

## 10. View Tasks
- **Description:** Users can view a list of their tasks.
- **Basic Flow:**
  1. User navigates to "My Tasks".
  2. System displays a list of tasks.

## 11. Edit Task
- **Description:** Users can edit an existing task.
- **Basic Flow:**
  1. User selects a task.
  2. User modifies task title/description/due date and linked notes/dependencies.
  3. System saves changes.

## 12. Delete Task
- **Description:** Users can delete a task.
- **Basic Flow:**
  1. User selects a task.
  2. User confirms deletion.
  3. System removes the task.

## 13. Complete Task
- **Description:** Users can mark a task as completed.
- **Basic Flow:**
  1. User selects a task.
  2. User marks the task as completed.
  3. System checks if all prerequisite tasks are completed.
  4. System update task status.

## 14. Create Tag
- **Description:** Users create a new tag.
- **Basic Flow:**
  1. User clicks "Create Tag".
  2. User enters tag title.
  3. System saves the tag.

## 15. View Tags
- **Description:** Users view a list of their tags.
- **Basic Flow:**
  1. User navigates to "My Tags".
  2. System displays a list of tags.

## 16. Edit Tag
- **Description:** Users can edit an existing tag.
- **Basic Flow:**
  1. User selects a tag.
  2. User modifies a tag title.
  3. System saves the changes.

## 17. Delete Tag
- **Description:** Users can delete a tag.
- **Basic Flow:**
  1. User selects a tag.
  2. System checks if the tag is linked to any note or task.
  3. If the tag is in use, system shows a warning to the user.
  4. User confirms deletion.
  5. System removes the tag from all linked notes and tasks.
  6. System deletes the tag.
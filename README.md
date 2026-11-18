# Ex03 To-Do List using JavaScript
## Date:17-11-2026

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
```html


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My To-Do List</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="app">

        <header>
            <div>
                <h1>My Tasks</h1>
                <p>Organize your day, one task at a time.</p>
            </div>

            <button id="themeBtn" class="theme-btn">🌙</button>
        </header>

        <section class="stats">
            <div class="stat-card">
                <h2 id="totalTasks">0</h2>
                <p>Total Tasks</p>
            </div>

            <div class="stat-card">
                <h2 id="pendingTasks">0</h2>
                <p>Pending</p>
            </div>

            <div class="stat-card">
                <h2 id="completedTasks">0</h2>
                <p>Completed</p>
            </div>
        </section>

        <section class="task-form">
            <h2>Add New Task</h2>

            <input
                type="text"
                id="taskInput"
                placeholder="What do you need to do?"
            >

            <label for="taskDate">Due Date & Time</label>

            <input type="datetime-local" id="taskDate">

            <button id="addBtn">+ Add Task</button>
        </section>

        <section class="task-section">

            <div class="task-heading">
                <h2>Your Tasks</h2>

                <select id="filterTasks">
                    <option value="all">All Tasks</option>
                    <option value="pending">Pending</option>
                    <option value="completed">Completed</option>
                </select>
            </div>

            <ul id="taskList"></ul>

            <p id="emptyMessage">
                No tasks yet. Add your first task!
            </p>

        </section>

        <footer>
            <p>Stay focused. Stay productive.</p>
        </footer>

    </div>

    <script src="script.js"></script>

</body>
</html>



```
```css


* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background: #eef2ff;
    color: #1e293b;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    padding: 40px 15px;
    transition: 0.3s;
}

.app {
    width: 100%;
    max-width: 650px;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 30px;
}

header h1 {
    font-size: 32px;
    margin-bottom: 8px;
}

header p {
    color: #64748b;
}

.theme-btn {
    border: none;
    background: white;
    padding: 12px;
    border-radius: 50%;
    font-size: 20px;
    cursor: pointer;
}

.stats {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
    margin-bottom: 25px;
}

.stat-card {
    background: white;
    padding: 20px;
    border-radius: 12px;
    text-align: center;
    box-shadow: 0 3px 12px #00000008;
}

.stat-card h2 {
    color: #4f46e5;
    font-size: 28px;
}

.stat-card p {
    color: #64748b;
    margin-top: 5px;
    font-size: 13px;
}

.task-form,
.task-section {
    background: white;
    padding: 25px;
    border-radius: 15px;
    margin-bottom: 20px;
    box-shadow: 0 3px 12px #00000008;
}

.task-form h2,
.task-heading h2 {
    margin-bottom: 18px;
    font-size: 20px;
}

input {
    width: 100%;
    padding: 13px;
    margin-bottom: 15px;
    border: 1px solid #cbd5e1;
    border-radius: 8px;
    outline: none;
    font-size: 14px;
    background: transparent;
    color: inherit;
}

input:focus {
    border-color: #4f46e5;
}

label {
    display: block;
    margin-bottom: 8px;
    font-size: 14px;
    font-weight: bold;
}

button {
    cursor: pointer;
}

#addBtn {
    width: 100%;
    padding: 13px;
    background: #4f46e5;
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 15px;
    font-weight: bold;
}

#addBtn:hover {
    background: #4338ca;
}

.task-heading {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

select {
    padding: 9px;
    border: 1px solid #cbd5e1;
    border-radius: 7px;
    background: transparent;
    color: inherit;
}

#taskList {
    list-style: none;
}

.task-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    background: #f8fafc;
    padding: 15px;
    margin-top: 12px;
    border-radius: 10px;
    animation: slideIn 0.3s ease;
}

@keyframes slideIn {
    from {
        opacity: 0;
        transform: translateY(10px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.task-info {
    flex: 1;
    min-width: 0;
}

.task-name {
    font-weight: bold;
    overflow-wrap: anywhere;
}

.task-date {
    color: #64748b;
    font-size: 12px;
    margin-top: 6px;
}

.completed .task-name {
    text-decoration: line-through;
    color: #94a3b8;
}

.task-actions {
    display: flex;
    gap: 6px;
}

.action-btn {
    border: none;
    padding: 8px;
    border-radius: 6px;
    color: white;
    font-size: 12px;
}

.done-btn {
    background: #16a34a;
}

.edit-btn {
    background: #f59e0b;
}

.delete-btn {
    background: #ef4444;
}

#emptyMessage {
    text-align: center;
    color: #94a3b8;
    padding: 25px 0;
}

footer {
    text-align: center;
    color: #94a3b8;
    font-size: 13px;
    margin-top: 25px;
}

/* DARK MODE */

body.dark {
    background: #0f172a;
    color: #f8fafc;
}

.dark .stat-card,
.dark .task-form,
.dark .task-section {
    background: #1e293b;
    color: white;
}

.dark .task-item {
    background: #334155;
}

.dark input,
.dark select {
    border-color: #475569;
    color: white;
}

.dark input::-webkit-calendar-picker-indicator {
    filter: invert(1);
}

.dark .theme-btn {
    background: #334155;
    color: white;
}

/* MOBILE RESPONSIVE */

@media (max-width: 500px) {
    body {
        padding: 25px 12px;
    }

    header h1 {
        font-size: 26px;
    }

    .stats {
        gap: 8px;
    }

    .stat-card {
        padding: 15px 5px;
    }

    .stat-card h2 {
        font-size: 23px;
    }

    .stat-card p {
        font-size: 11px;
    }

    .task-form,
    .task-section {
        padding: 18px;
    }

    .task-item {
        flex-wrap: wrap;
    }

    .task-actions {
        width: 100%;
        justify-content: flex-end;
    }
}

```
```javascript


let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

let darkMode = localStorage.getItem("darkMode") === "true";

const taskInput = document.getElementById("taskInput");
const taskDate = document.getElementById("taskDate");
const taskList = document.getElementById("taskList");
const addBtn = document.getElementById("addBtn");
const themeBtn = document.getElementById("themeBtn");
const filterTasks = document.getElementById("filterTasks");

// SAVE TASKS
function saveTasks() {
    localStorage.setItem("tasks", JSON.stringify(tasks));
}

// ADD TASK
function addTask() {
    let taskName = taskInput.value.trim();

    if (taskName === "") {
        alert("Please enter a task!");
        return;
    }

    let task = {
        id: Date.now(),
        name: taskName,
        date: taskDate.value,
        completed: false
    };

    tasks.push(task);

    saveTasks();
    displayTasks();

    taskInput.value = "";
    taskDate.value = "";
}

addBtn.addEventListener("click", addTask);

// ADD TASK USING ENTER KEY
taskInput.addEventListener("keydown", function(event) {
    if (event.key === "Enter") {
        addTask();
    }
});

// DISPLAY TASKS
function displayTasks() {

    taskList.innerHTML = "";

    let filter = filterTasks.value;

    let filteredTasks = tasks.filter(task => {
        if (filter === "pending") {
            return !task.completed;
        }

        if (filter === "completed") {
            return task.completed;
        }

        return true;
    });

    document.getElementById("totalTasks").textContent =
        tasks.length;

    document.getElementById("pendingTasks").textContent =
        tasks.filter(task => !task.completed).length;

    document.getElementById("completedTasks").textContent =
        tasks.filter(task => task.completed).length;

    document.getElementById("emptyMessage").style.display =
        filteredTasks.length === 0 ? "block" : "none";

    filteredTasks.forEach(task => {

        let li = document.createElement("li");

        li.className = "task-item";

        if (task.completed) {
            li.classList.add("completed");
        }

        let info = document.createElement("div");
        info.className = "task-info";

        let name = document.createElement("p");
        name.className = "task-name";
        name.textContent = task.name;

        let date = document.createElement("p");
        date.className = "task-date";

        if (task.date) {
            let dateValue = new Date(task.date);

            date.textContent =
                "Due: " + dateValue.toLocaleString();
        } else {
            date.textContent = "No due date";
        }

        info.appendChild(name);
        info.appendChild(date);

        // ACTION BUTTONS
        let actions = document.createElement("div");
        actions.className = "task-actions";

        // COMPLETE BUTTON
        let doneBtn = document.createElement("button");
        doneBtn.className = "action-btn done-btn";
        doneBtn.textContent = task.completed ? "Undo" : "Done";

        doneBtn.onclick = function() {
            task.completed = !task.completed;
            saveTasks();
            displayTasks();
        };

        // EDIT BUTTON
        let editBtn = document.createElement("button");
        editBtn.className = "action-btn edit-btn";
        editBtn.textContent = "Edit";

        editBtn.onclick = function() {
            let newName = prompt("Edit your task:", task.name);

            if (newName !== null && newName.trim() !== "") {
                task.name = newName.trim();
                saveTasks();
                displayTasks();
            }

            if (newName !== null && newName.trim() === "") {
                alert("Task cannot be empty!");
            }
        };

        // DELETE BUTTON
        let deleteBtn = document.createElement("button");
        deleteBtn.className = "action-btn delete-btn";
        deleteBtn.textContent = "Delete";

        deleteBtn.onclick = function() {
            if (confirm("Are you sure you want to delete this task?")) {
                tasks = tasks.filter(t => t.id !== task.id);
                saveTasks();
                displayTasks();
            }
        };

        actions.appendChild(doneBtn);
        actions.appendChild(editBtn);
        actions.appendChild(deleteBtn);

        li.appendChild(info);
        li.appendChild(actions);

        taskList.appendChild(li);

    });
}

// FILTER TASKS
filterTasks.addEventListener("change", displayTasks);

// DARK AND LIGHT MODE
function applyTheme() {
    document.body.classList.toggle("dark", darkMode);

    themeBtn.textContent = darkMode ? "☀️" : "🌙";

    localStorage.setItem("darkMode", darkMode);
}

themeBtn.addEventListener("click", function() {
    darkMode = !darkMode;
    applyTheme();
});

// INITIAL LOAD
applyTheme();
displayTasks();


```


## OUTPUT

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/f062fe20-2377-4fb9-9460-00f5aa8803df" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.

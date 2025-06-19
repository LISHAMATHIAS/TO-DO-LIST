<!DOCTYPE html>
<html>
<head>
  <title>TO DO List</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f2f2f2;
    }
    
    .container {
      max-width: 400px;
      margin: 0 auto;
      padding: 20px;
      background-color: #fff;
      box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
    }
    
    .header {
      text-align: center;
      margin-bottom: 20px;
    }
    
    .task-input {
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    
    .task-list {
      list-style-type: none;
      padding: 0;
    }
    
    .task-list li {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 10px;
      background-color: #f2f2f2;
      border-radius: 4px;
      margin-bottom: 5px;
    }
    
    .task-list li .task {
      flex-grow: 1;
    }
    
    .task-list li .edit-btn,
    .task-list li .delete-btn {
      background-color: #4286f4;
      color: #fff;
      border: none;
      padding: 5px 10px;
      border-radius: 4px;
      cursor: pointer;
    }
    
    .task-list li .edit-btn {
      margin-right: 5px;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <h1>TO DO List</h1>
    </div>
    
    <input id="task-input" class="task-input" type="text" placeholder="Enter a task">
    <button id="add-btn">Add Task</button>
    <ul id="task-list" class="task-list"></ul>
  </div>

  <script>
    // Get elements
    const taskInput = document.getElementById('task-input');
    const addBtn = document.getElementById('add-btn');
    const taskList = document.getElementById('task-list');

    // Add task function
    function addTask() {
      const task = taskInput.value;
      if (task.trim() === '') return;

      const li = document.createElement('li');
      li.innerHTML = `
        <span class="task">${task}</span>
        <button class="edit-btn">Edit</button>
        <button class="delete-btn">Delete</button>
      `;

      taskList.appendChild(li);
      taskInput.value = '';
    }

    // Edit task function
    function editTask(e) {
      const taskSpan = e.target.previousElementSibling;
      const newTask = prompt('Edit task:', taskSpan.innerText);

      if (newTask && newTask.trim() !== '') {
        taskSpan.innerText = newTask;
      }
    }

    // Delete task function
    function deleteTask(e) {
      if (e.target.classList.contains('delete-btn')) {
        e.target.parentElement.remove();
      }
    }

    // Event listeners
    addBtn.addEventListener('click', addTask);

    taskList.addEventListener('click', function (e) {
      if (e.target.classList.contains('edit-btn')) {
        editTask(e);
      } else if (e.target.classList.contains('delete-btn')) {
        deleteTask(e);
      }
    });
  </script>
</body>
</html># TO-DO-LIST

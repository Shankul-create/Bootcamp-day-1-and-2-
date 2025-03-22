const body = document.body;
body.innerHTML = `
  <div class="container">
    <h1>To-Do List</h1>
    <div class="input-section">
      <input type="text" id="taskInput" placeholder="Enter a new task" />
      <button id="addTaskButton">Add Task</button>
    </div>
    <ul id="taskList"></ul>
  </div>
`;

// CSS styling
const style = document.createElement('style');
style.textContent = `
  body {
    font-family: Arial, sans-serif;
    background-color: #f0f8ff;
    margin: 0;
    padding: 20px;
  }
  .container {
    max-width: 500px;
    margin: 0 auto;
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  h1 {
    text-align: center;
  }
  .input-section {
    display: flex;
    gap: 10px;
  }
  #taskInput {
    flex: 1;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  #addTaskButton {
    padding: 8px 16px;
    background-color: #007BFF;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  #addTaskButton:hover {
    background-color: #0056b3;
  }
  ul {
    list-style: none;
    padding: 0;
  }
  li {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    background: #f9f9f9;
    margin-top: 8px;
    border-radius: 4px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  .delete-button {
    background-color: #dc3545;
    color: white;
    border: none;
    border-radius: 4px;
    padding: 4px 8px;
    cursor: pointer;
  }
  .delete-button:hover {
    background-color: #a71d2a;
  }
`;
document.head.appendChild(style);

// JavaScript functionality
const taskInput = document.getElementById('taskInput');
const addTaskButton = document.getElementById('addTaskButton');
const taskList = document.getElementById('taskList');

addTaskButton.addEventListener('click', () => {
  const taskText = taskInput.value.trim();
  if (taskText) {
    const li = document.createElement('li');
    li.innerHTML = `
      <span>${taskText}</span>
      <button class="delete-button">Delete</button>
    `;
    
    const deleteButton = li.querySelector('.delete-button');
    deleteButton.addEventListener('click', () => {
      li.remove();
    });

    taskList.appendChild(li);
    taskInput.value = '';
  }
});

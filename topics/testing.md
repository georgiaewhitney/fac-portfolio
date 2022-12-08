# Testing portfolio

## 1. Check that passing a given input into our tests returns the expected output

The [workshops](https://) throughout the testing module helped us understand how to implement testing by creating functions that check through a minimum expected / actual set of values. 

```js    
function equal(actual, expected, message) {
  if (actual === expected) {
    const defaultMessage = `Expected ${expected} and received ${actual}`;
    console.info("Pass: " + (message || defaultMessage));
  } else {
    const defaultMessage = `Expected ${expected} but received ${actual} instead`;
    console.error("Fail: " + (message || defaultMessage));
  }
}
```

## 2. Write tests to mimic the behaviour of a user performing different actions

We wrote tests to check the core functions of the application. 

In this case, we tested how a task can be added to the list.

```js    
test("Can a user add a new task to the list?", () => {
  // 1. Create a new task
  const input = document.querySelector("#to-do");
  input.value = `This is a task`;
  const submitButton = document.querySelector("#submit-btn");
  submitButton.click();

// 2. Grab all the li elements in the DOM to see how many tasks have been created
const currentTasks = document.querySelectorAll(".listItem");

// 3. Check the length of the list;
NumOfTasks = currentTasks.length;

// 4. Compare the number of tasks in the DOM with the expected number
equal(NumOfTasks, 1);

// 5. Reset DOM 
const removeButtons = document.querySelectorAll(".remove-task-btn");
removeButtons.forEach(button => button.click())
})
```


## 3. Write testable, modular functions

During the initial stages of planning the app, to explore functionality options, I didn't write the JavaScript with TDD in mind. This caused confusion in testing early on, and provided a good opportunity to learn TDD's value. 

As we then refactored the script, we implemented TDD and considered functions among this. The functions were more descriptive and better understood. For example, functionality to add tasks, delete tasks, and then to add to local storage. 

Shortened, here's the intiial create task functionality. 

```js   
// <========== Function allows user to create a new task  ==========> 
const addTaskItem = () => {
...
};
```

## 4. Write functions that add, remove or modify DOM nodes

Due to the nature of the app, a large portion of the functionality added, removed, and edited DOM nodes. 

Here, this function allows the user to create a new task that is created on their do-do list. It creates an `<li>` element containing the data submitted by the user, adding the checkbox/checked and delete functionality within it, and then assigns it a number which will allow us to edit it later. 

```js 
const addTaskItem = () => {
  // Create a new <li> element and give it a class and unique ID
  const taskItem = document.createElement("li");
  taskItem.classList = "listItem";
  const taskNum = new Date().getTime().toString();
  taskItem.dataset.taskNum = taskNum;

  if (input.value === "") return;

  // Create the content inside the <li> element
  taskItem.innerHTML = `
  <input aria-label="Mark task as complete" type="checkbox"/>
  <span>${input.value}</span>
  <button type="button" class="remove-task-btn"><i class="fa-solid fa-x"></i></button>
  `;
  ```


## 5. Apply event listeners to HTML form elements

We used event listeners to manage click functionality through the app - deleting, submitting, and even clicking the checkbox for 'task complete' functionality. 

```js    
// Attach event listener to checkbox so that user can toggle completed state
  const checkbox = taskItem.querySelector("input[type='checkbox']");
  checkbox.addEventListener("click", (e) => {
    markTaskAsComplete(e.target);
  })
  if (task.completed === true){ // if the task's completed status is true, check the box so user doesn't have to retick it
    checkbox.checked = true;
  }
  // allows the X button to delete with the function below
  const removeTaskButton = taskItem.querySelector(".remove-task-btn");
  removeTaskButton.addEventListener("click", (e) => {
    deleteTask(e.target);
  });
```

## 6. Use scope to control what variables are accessible inside functions and blocks

Our script used mostly block scope to keep the code and functionality readable and easier to manage. 

For example, within the function to create a task, the newTask object is declared within the function to streamline the scope of when this object should be used. 

```js    
// Create an object made up of the: 1) task's description; 2) task's status; 3) task's ID
  const newTask = {
    description: input.value,
    completed: false,
    id: taskNum,
  }
 ```
 
 We use some global variables to grab elements from the HTML for ease. 
 
 ```js        
 // grabs input
const input = document.querySelector("input");
// grabs list
const list = document.querySelector(".list");
// grabs submit button
const submitBtn = document.getElementById("submit-btn");
// Array to store user's tasks
let userTasks = JSON.parse(localStorage.getItem("userTasks")) || [];
```
 

## 7. Use CSS grid to create complex layouts

We didn't use CSS grid for this project. We opted for flexbox. 

```css
#to-do-input {
  display: flex;
  width: 100%;
  gap: 5px;
}
```
## 8. Use CSS grid to make layouts that adapt to the viewport size

While we didn't use CSS grid, our application still adapts to the viewport size comfortably, using `max-width` and `@media enquiries` via CSS. 

```css    
@media all and (max-width: 500px) {
  body {
    padding: 0;
  }
```


# ES5 Lesson Plan: Core JavaScript Concepts

Here's a comprehensive lesson plan covering your requested topics for ES5 JavaScript. Each section includes explanations, examples, and practical exercises.

## 1. Understanding 'this' in JavaScript

**Objective**: Explain how the `this` keyword works in different contexts.

### Concepts:
- Global context: `this` refers to the window object
- Function context: depends on how the function is called
- Method context: `this` refers to the object the method belongs to
- Constructor context: `this` refers to the newly created object


### Examples:
```javascript
// Global context
console.log(this); // Window object

// Function context
function showThis() {
  console.log(this);
}
showThis(); // Window in non-strict mode, undefined in strict mode

// Method context
var obj = {
  name: "My Object",
  showThis: function() {
    console.log(this);
  }
};
obj.showThis(); // obj

// Constructor context
function Person(name) {
  this.name = name;
}
var person = new Person("Alice");
console.log(person.name); // "Alice"



### Exercise:
Create an object with a method that uses `this`. Then create another object and use `call()` to invoke the method with the second object as context.

## 2. Mouse Events in JavaScript

**Objective**: Handle mouse interactions in the browser.

### Concepts:
- Common mouse events: `click`, `dblclick`, `mousedown`, `mouseup`, `mousemove`, `mouseover`, `mouseout`
- Event object properties: `clientX`, `clientY`, `target`, `button`
- Event bubbling and capturing
- Preventing default behavior with `preventDefault()`
- Stopping propagation with `stopPropagation()`

### Examples:
```javascript
// Adding event listeners
var button = document.getElementById('myButton');
button.addEventListener('click', function(event) {
  console.log('Clicked at:', event.clientX, event.clientY);
});

// Event delegation
document.addEventListener('click', function(event) {
  if (event.target.classList.contains('item')) {
    console.log('Item clicked:', event.target.textContent);
  }
});

// Preventing default
var link = document.getElementById('myLink');
link.addEventListener('click', function(event) {
  event.preventDefault();
  console.log('Link click prevented');
});
```

### Exercise:
Create a simple drawing app that tracks mouse movements and draws dots when the mouse is clicked and dragged.

## 3. querySelector and DOM Manipulation

**Objective**: Select and manipulate DOM elements efficiently.

### Concepts:
- `querySelector()` vs `querySelectorAll()`
- Differences from `getElementById()` and `getElementsByClassName()`
- Traversing the DOM: `parentNode`, `childNodes`, `nextSibling`, etc.
- Creating and inserting elements: `createElement()`, `appendChild()`, `insertBefore()`
- Removing elements: `removeChild()`

### Examples:
```javascript
// Selecting elements
var firstItem = document.querySelector('.item');
var allItems = document.querySelectorAll('.item');

// Creating and adding elements
var newDiv = document.createElement('div');
newDiv.textContent = 'New Element';
newDiv.className = 'box';
document.body.appendChild(newDiv);

// Removing elements
var oldDiv = document.querySelector('.old');
if (oldDiv) {
  oldDiv.parentNode.removeChild(oldDiv);
}

// Modifying attributes
var image = document.querySelector('img');
image.setAttribute('alt', 'New description');
```

### Exercise:
Build a simple to-do list where users can add new items and remove existing ones.

## 4. Dynamic Styling with JavaScript

**Objective**: Modify element styles programmatically.

### Concepts:
- Accessing styles with `element.style`
- Working with CSS classes: `classList` methods (`add`, `remove`, `toggle`, `contains`)
- Getting computed styles with `getComputedStyle()`
- Best practices for dynamic styling

### Examples:
```javascript
// Inline styles
var box = document.querySelector('.box');
box.style.backgroundColor = 'blue';
box.style.width = '100px';

// Class manipulation
box.classList.add('highlight');
box.classList.remove('inactive');
box.classList.toggle('visible');

// Getting computed styles
var styles = window.getComputedStyle(box);
console.log(styles.getPropertyValue('width'));

// Animating with JavaScript
function animate() {
  var pos = 0;
  var id = setInterval(frame, 10);
  function frame() {
    if (pos == 350) {
      clearInterval(id);
    } else {
      pos++;
      box.style.left = pos + 'px';
    }
  }
}
```
### Exercise:
Create a button that toggles between light and dark mode for a webpage by changing styles.


# **Deep Dive: setTimeout, setInterval, and Asynchronous Timing in JavaScript (ES5)**

## **1. Understanding JavaScript's Event Loop**
JavaScript is **single-threaded**, meaning it executes one operation at a time. However, it uses **asynchronous callbacks** to handle delays and repeated tasks without blocking the main thread.

### **Key Concepts:**
- **Call Stack:** Where synchronous code executes.
- **Web APIs:** Browser-provided features (`setTimeout`, `setInterval`, `fetch`, etc.).
- **Callback Queue:** Holds callbacks waiting to be executed.
- **Event Loop:** Continuously checks if the call stack is empty and moves callbacks from the queue to the stack.

![Event Loop Diagram](https://miro.medium.com/v2/resize:fit:720/format:webp/1*FA9NGxNB6-v1oI2qGEtlRQ.png)

---

## **2. setTimeout() – Delayed Execution**
Executes a function **once** after a specified delay (in milliseconds).

### **Syntax:**
```javascript
setTimeout(callback, delay, [arg1], [arg2], ...);
```
- `callback`: Function to execute.
- `delay`: Time in milliseconds (default `0`).
- `arg1, arg2, ...`: Optional arguments passed to the callback.

### **Examples:**

#### **Example 1: Basic setTimeout**
```javascript
console.log("Start");

setTimeout(function() {
  console.log("This runs after 2 seconds");
}, 2000);

console.log("End");
```
**Output:**
```
Start
End
This runs after 2 seconds
```

#### **Example 2: Passing Arguments**
```javascript
setTimeout(function(name, age) {
  console.log(`Hello, ${name}! You are ${age} years old.`);
}, 1000, "Alice", 25);
```
**Output (after 1 second):**
```
Hello, Alice! You are 25 years old.
```

#### **Example 3: Clearing a Timeout**
```javascript
const timeoutId = setTimeout(() => {
  console.log("This will never run");
}, 2000);

clearTimeout(timeoutId); // Cancels the timeout
```

---

## **3. setInterval() – Repeated Execution**
Executes a function **repeatedly** at a given interval.

### **Syntax:**
```javascript
setInterval(callback, interval, [arg1], [arg2], ...);
```
- `interval`: Time in milliseconds between executions.

### **Examples:**

#### **Example 1: Basic setInterval**
```javascript
let counter = 0;
const intervalId = setInterval(function() {
  counter++;
  console.log(`Tick ${counter}`);
  
  if (counter >= 5) {
    clearInterval(intervalId); // Stop after 5 ticks
  }
}, 1000);
```
**Output (every second):**
```
Tick 1
Tick 2
Tick 3
Tick 4
Tick 5
```

#### **Example 2: Dynamic Interval Adjustment**
```javascript
let speed = 1000; // Start with 1-second interval
let counter = 0;

const intervalId = setInterval(function() {
  counter++;
  console.log(`Message ${counter}`);
  
  if (counter % 3 === 0) {
    clearInterval(intervalId); // Stop current interval
    speed -= 200; // Speed up by 200ms
    if (speed > 0) {
      setInterval(arguments.callee, speed); // Restart with new speed
    }
  }
}, speed);
```
**Output (speeds up every 3 messages):**
```
Message 1 (after 1s)
Message 2 (after 2s)
Message 3 (after 3s)
Message 4 (after 3.8s) // Now faster
Message 5 (after 4.6s)
...
```

---

## **4. Asynchronous Timing Patterns**
### **Pattern 1: Chaining setTimeout for Precise Timing**
Instead of `setInterval`, sometimes `setTimeout` chaining is more reliable (avoids drift).

```javascript
let counter = 0;

function delayedLoop() {
  setTimeout(function() {
    counter++;
    console.log(`Counter: ${counter}`);
    
    if (counter < 5) {
      delayedLoop(); // Recursively call
    }
  }, 1000);
}

delayedLoop();
```
**Output (every 1 second):**
```
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
```
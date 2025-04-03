

# **JavaScript ES5 Deep Dive with Examples**  

---

## **1. Introduction to ES5**  
### **Why ES5?**  
- Legacy codebases, browser compatibility.  
- Foundational for understanding modern JS quirks.  

**Example: ES5 vs ES6**  
```javascript
// ES5
var name = "Alice";
function greet() { return "Hello " + name; }

// ES6 (contrast only)
const name = "Alice";
const greet = () => `Hello ${name}`;
```

---

## **2. Variables, Types & Operators**  
### **A. `var` Scoping**  
```javascript

var x = 5;
var y = 6;
var z = x + y;

function test() {
  if (true) {
    var x = 10; // Leaks outside block!
  }
  console.log(x); // 10 (not block-scoped)
}
test();
```

### **B. Type Coercion Pitfalls**  
```javascript
console.log(1 + "1");     // "11" (string concatenation)
console.log("5" - 2);     // 3 (numeric subtraction)
console.log(null == undefined); // true (loose equality)
```

**Exercise:** Predict outputs:  
```javascript
console.log([] + []);               // "" (empty string)
console.log("2" * "3");             // 6 (numeric multiplication)
```

---

## **3. Functions**  
### **A. Function Declaration vs Expression**  
```javascript
// Declaration (hoisted)
sayHello(); // Works!
function sayHello() { console.log("Hi!"); }

// Expression (not hoisted)
sayHi(); // Error: sayHi is not a function
var sayHi = function() { console.log("Hi!"); };
```

### **B. `arguments` Object**  
```javascript
function logArgs() {
  console.log(arguments); // { 0: "a", 1: "b", length: 2 }
}
logArgs("a", "b");
```

**Exercise:** Create a function `concatAll()` that joins all arguments into a string.  
**Solution:**  
```javascript
function concatAll() {
  var result = "";
  for (var i = 0; i < arguments.length; i++) {
    result += arguments[i];
  }
  return result;
}
concatAll("Hello", " ", "World"); // "Hello World"
```

---

## **4. Click Events**  
### **Inline vs Unobtrusive**  
```html
<!-- Inline (avoid) -->
<button onclick="alert('Clicked!')">Click</button>

<!-- Best practice -->
<button id="myBtn">Click</button>
<script>
  document.getElementById("myBtn").onclick = function() {
    console.log("Button clicked!");
  };
</script>
```

**Exercise:** Build a counter button.  
**Solution:**  
```javascript
var count = 0;
document.getElementById("counterBtn").onclick = function() {
  count++;
  document.getElementById("countDisplay").textContent = count;
};
```

---

## **5. Understanding `this`**  
### **Context Rules**  
```javascript
// Global context
console.log(this); // Window (in browsers)

// Object method
var obj = {
  name: "Alice",
  greet: function() { console.log(this.name); }
};
obj.greet(); // "Alice"

// Event handler
button.onclick = function() { 
  console.log(this); // <button> element 
};
```

### **Pitfall & Fix**  
```javascript
var obj = {
  name: "Bob",
  greet: function() {
    setTimeout(function() {
      console.log(this.name); // Undefined (lost context)
    }, 100);
  }
};
// Fix:
var obj = {
  name: "Bob",
  greet: function() {
    var self = this; // Preserve context
    setTimeout(function() {
      console.log(self.name); // "Bob"
    }, 100);
  }
};
```

---

## **6. Hover Events**  
### **`mouseover` & `mouseout`**  
```javascript
var box = document.getElementById("box");
box.onmouseover = function() {
  this.style.backgroundColor = "red";
};
box.onmouseout = function() {
  this.style.backgroundColor = "blue";
};
```

**Exercise:** Create a tooltip on hover.  
**Solution:**  
```javascript
var tooltip = document.createElement("div");
tooltip.textContent = "Hover info!";
tooltip.style.display = "none";
document.body.appendChild(tooltip);

element.onmouseover = function() {
  tooltip.style.display = "block";
};
element.onmouseout = function() {
  tooltip.style.display = "none";
};
```

---

## **7. `querySelector`**  
### **Single vs Multiple Elements**  
```javascript
// Single element
var el = document.querySelector(".class"); // First match

// All elements
var buttons = document.querySelectorAll("button"); // NodeList
buttons.forEach(function(button) { // Note: forEach works on NodeLists
  button.style.color = "red";
});
```

**Exercise:** Highlight every other table row.  
**Solution:**  
```javascript
var rows = document.querySelectorAll("tr:nth-child(odd)");
rows.forEach(function(row) {
  row.style.backgroundColor = "#f2f2f2";
});
```

---

## **8. Changing HTML & CSS**  
### **Dynamic Styling**  
```javascript
// CSS
var div = document.querySelector("div");
div.style.cssText = "color: red; font-size: 20px;";

// HTML
div.innerHTML = "<strong>New content</strong>";
```

**Exercise:** Build a theme switcher (light/dark mode).  
**Solution:**  
```javascript
document.getElementById("themeBtn").onclick = function() {
  var body = document.body;
  body.style.backgroundColor = 
    body.style.backgroundColor === "black" ? "white" : "black";
};
```

---

## **Recap Cheat Sheet**  
| Concept                | Example                                      | Key Insight                          |
|------------------------|----------------------------------------------|--------------------------------------|
| **`var` Scoping**      | `if (true) { var x=10; } console.log(x); // 10` | Leaks outside blocks!               |
| **`this` Pitfall**     | `setTimeout(function() { console.log(this); }, 100);` | Loses context, use `self` trick.    |
| **Hover Events**       | `element.onmouseover = function() { ... };`  | Pair with `mouseout`.               |
| **`querySelectorAll`** | `document.querySelectorAll("li").forEach(...);` | Returns NodeList (not Array).       |

---

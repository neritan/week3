
# **Complete Lesson: Terminal, Git/GitHub & JavaScript ES5**  

---

## **1. Terminal Basics**  
### **Key Commands**  
```bash
# Navigation
pwd           # Show current directory
ls            # List files/folders
cd ~/Desktop  # Navigate to Desktop
mkdir project # Create folder
touch app.js  # Create file

# File Operations
cp file.txt backup.txt  # Copy
mv old.txt new.txt      # Rename/move
rm file.txt            # Delete file
rm -r folder/          # Delete folder (recursive)

# Permissions
chmod +x script.sh    # Make file executable
```

### **Exercise**  
1. Create a folder `web_dev` and a file `index.html` inside it.  
2. Rename the file to `home.html`.  

**Solution:**  
```bash
mkdir web_dev
cd web_dev
touch index.html
mv index.html home.html
```

---

## **2. Git & GitHub**  
### **Step-by-Step Workflow**  
#### **A. Local Repo Setup**  
```bash
git init                    # Initialize repo
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

#### **B. Stage & Commit**  
```bash
git add .                   # Stage all changes
git add file.txt            # Stage specific file
git commit -m "Initial commit"  
```

#### **C. Connect to GitHub**  
1. Create a **new repo** on GitHub (no README/license).  
2. Link and push:  
```bash
git remote add origin https://github.com/username/repo.git
git branch -M main          # Rename default branch
git push -u origin main     # First push
```

### **Key Commands**  
```bash
git status                  # Check changes
git log                     # View commit history
git clone <repo-url>        # Download repo
git pull                    # Fetch + merge changes
```

### **Exercise**  
1. Create a `README.md` file, commit, and push to GitHub.  
**Solution:**  
```bash
echo "# My Project" > README.md
git add README.md
git commit -m "Added README"
git push
```

### **Troubleshooting**  
| Issue | Fix |
|-------|-----|
| `git push` fails | Use a GitHub [PAT (Personal Access Token)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) instead of password. |
| Merge conflict | Edit conflicted file, then `git add .` + `git commit`. |

---

## **3. JavaScript ES5**  
### **Core Concepts**  
#### **Variables & Scope**  
```javascript
var x = 5;                  // Function-scoped
if (true) { var y = 10; }   // Leaks outside block
console.log(y);             // 10
```

#### **Functions**  
```javascript
// Function Declaration (hoisted)
function greet() { return "Hello!"; }

// Function Expression
var greet = function() { return "Hello!"; };

// Arguments Object
function sum() {
  var total = 0;
  for (var i = 0; i < arguments.length; i++) {
    total += arguments[i];
  }
  return total;
}
sum(1, 2, 3); // 6
```

#### **DOM Manipulation**  
```html
<button id="btn">Click Me</button>
<script>
  var btn = document.getElementById("btn");
  btn.onclick = function() {
    alert("Clicked!");
  };
</script>
```

### **Exercise**  
Create a button that toggles a div’s text color between red and blue.  
**Solution:**  
```html
<button id="colorBtn">Toggle Color</button>
<div id="text">Hello World!</div>
<script>
  var btn = document.getElementById("colorBtn");
  var text = document.getElementById("text");
  btn.onclick = function() {
    text.style.color = text.style.color === "red" ? "blue" : "red";
  };
</script>
```

---

## **4. Lesson Recap**  
### **Terminal**  
- Navigate, create, and manage files via commands.  

### **Git/GitHub**  
- `init` → `add` → `commit` → `push` → `pull`.  
- Always `git status` to check state.  

### **JavaScript ES5**  
- `var` is function-scoped, `function` declarations are hoisted.  
- Use `document.getElementById()` for DOM.  

---

## **5. Homework/Quiz**  
1. **Terminal**: Create a folder `quiz` with 3 files (`q1.txt`, `q2.txt`, `q3.txt`).  
2. **Git**: Clone any GitHub repo, add a file, and create a pull request.  
3. **JS**: Write an ES5 function `multiply(a, b)` using `arguments`.  

**Need solutions?** Here’s the JS answer:  
```javascript
function multiply() {
  return arguments[0] * arguments[1];
}
multiply(2, 3); // 6
```

---

### **Bonus: Quick-Reference Table**  
| Tool | Command/Code | Use Case |
|------|-------------|----------|
| Terminal | `mv old.txt new.txt` | Rename files |
| Git | `git log --oneline` | Compact commit history |
| JS ES5 | `var arr = [1, 2].map(function(x) { return x * 2; });` | Double array values |

---

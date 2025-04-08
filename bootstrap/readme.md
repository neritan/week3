# Introduction to Bootstrap in HTML

By the end of this lesson, learners will understand what Bootstrap is, how to include it in an HTML project, and how to use its basic components to create a responsive webpage.
Duration

## 1. What is Bootstrap?
Definition: Bootstrap is a free, open-source CSS framework for building responsive and mobile-first websites.
Purpose: It simplifies web design by providing pre-built CSS and JavaScript components (e.g., buttons, forms, navigation bars) so developers don’t have to start from scratch.
Key Features:
Responsive grid system
Pre-styled components (e.g., buttons, cards, modals)
Cross-browser compatibility
## 2. Setting Up Bootstrap in HTML
To use Bootstrap, you need to include its CSS and JavaScript files in your HTML document. There are two main ways to do this:
CDN (Content Delivery Network): Quick and easy, no local files needed.
Download: For offline use or customizations.
Example: Using Bootstrap via CDN
html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bootstrap Lesson</title>
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <h1>Hello, Bootstrap!</h1>
    <!-- Bootstrap JS (Optional, needed for interactive components) -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```
Explanation:

The CSS link adds Bootstrap styles.
The JS script (optional) enables interactive features like dropdowns or modals.
## 3. Bootstrap Grid System
Bootstrap uses a 12-column grid system to create responsive layouts.
Classes:
.container: Centers content with padding.
.row: Creates a horizontal group of columns.
.col: Defines columns (e.g., .col-6 takes up half the width).
Example: Simple Grid Layout

```html
<div class="container">
    <div class="row">
        <div class="col-6">
            <p>This is the left half.</p>
        </div>
        <div class="col-6">
            <p>This is the right half.</p>
        </div>
    </div>
</div>
```
Result: Two equal-width columns side by side.
Responsive Tip: Use breakpoints like .col-md-6 to adjust layouts for different screen sizes (e.g., md for medium screens).
## 4. Common Bootstrap Components
Bootstrap offers ready-to-use components. Let’s try a few:
### a) Buttons
```html
<button class="btn btn-primary">Primary Button</button>
<button class="btn btn-success">Success Button</button>
<button class="btn btn-danger">Danger Button</button>
```
Classes: .btn (base style) + modifiers like .btn-primary, .btn-success.
### b) Navbar
```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container">
        <a class="navbar-brand" href="#">My Website</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
                <li class="nav-item">
                    <a class="nav-link" href="#">Home</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">About</a>
                </li>
            </ul>
        </div>
    </div>
</nav>
```
Note: Requires Bootstrap JS for the toggle functionality.
### c) Card
```html
<div class="card" style="width: 18rem;">
    <div class="card-body">
        <h5 class="card-title">Card Title</h5>
        <p class="card-text">This is a simple card example.</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
    </div>
</div>
```
## 5. Practice Activity
Let create a simple webpage with:
A responsive navbar.
A two-column layout using the grid system.
A button and a card in one of the columns.
Starter Code
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Bootstrap Page</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <!-- Add your navbar here -->
    <div class="container">
        <div class="row">
            <div class="col-md-6">
                <!-- Add content here -->
            </div>
            <div class="col-md-6">
                <!-- Add content here -->
            </div>
        </div>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```
## 6. Wrap-Up
Key Takeaways:
Bootstrap makes responsive design easier with its grid and components.
Use the CDN for quick setup or download for offline work.
Explore the Bootstrap documentation for more features.
Homework: Build a personal portfolio page using Bootstrap’s grid, navbar, and cards.
Would you like me to expand on any section, provide more examples, or help you tweak this for a specific audience (e.g., students, professionals)? Let me know!
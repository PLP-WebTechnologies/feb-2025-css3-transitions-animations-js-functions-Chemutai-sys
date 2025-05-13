# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨
index.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Animation & Storage Playground</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <header>
    <h1>💫 Animation & Storage Playground</h1>
  </header>

  <main>
    <!-- Animated Button -->
    <section>
      <button id="animate-btn">Animate Me!</button>
      <div id="animated-box"></div>
    </section>

    <!-- Theme Preference -->
    <section>
      <h2>Choose Theme</h2>
      <button onclick="setTheme('light')">Light</button>
      <button onclick="setTheme('dark')">Dark</button>
      <p id="theme-status"></p>
    </section>
  </main>

  <script src="script.js"></script>
</body>
</html>

style.css

body {
  font-family: Arial, sans-serif;
  padding: 20px;
  transition: background-color 0.5s, color 0.5s;
}

button {
  padding: 10px 15px;
  margin: 10px;
  cursor: pointer;
  transition: transform 0.3s ease;
}

button:hover {
  transform: scale(1.1);
}

#animated-box {
  width: 100px;
  height: 100px;
  background-color: teal;
  margin-top: 20px;
  transition: all 0.5s ease;
  position: relative;
}

.animate-move {
  animation: slide 1s forwards;
}

@keyframes slide {
  0% { left: 0; background-color: teal; }
  100% { left: 300px; background-color: coral; }
}

/* Themes */
body.light-theme {
  background-color: #ffffff;
  color: #000000;
}

body.dark-theme {
  background-color: #222222;
  color: #f1f1f1;
}

script.js

// Animation trigger
document.getElementById('animate-btn').addEventListener('click', () => {
  const box = document.getElementById('animated-box');
  box.classList.remove('animate-move'); // restart animation if applied
  void box.offsetWidth; // trigger reflow to reset animation
  box.classList.add('animate-move');
});

// Theme preference with localStorage
function setTheme(theme) {
  localStorage.setItem('preferredTheme', theme);
  applyTheme(theme);
}

function applyTheme(theme) {
  document.body.classList.remove('light-theme', 'dark-theme');
  document.body.classList.add(`${theme}-theme`);
  document.getElementById('theme-status').textContent = `Current theme: ${theme}`;
}

// Load theme from localStorage on page load
document.addEventListener('DOMContentLoaded', () => {
  const storedTheme = localStorage.getItem('preferredTheme') || 'light';
  applyTheme(storedTheme);
});

# Svelte 5 To-Do List (Beginner Project)

This repository contains a beginner-friendly To-Do List application built with **Svelte 5** and **Vite**. It was designed specifically to help transition from visual block-based programming (like MIT App Inventor) to modern web development frameworks.

## 🚀 Getting Started

To run this project on your local machine:

1. Open your terminal and navigate to the project folder:
   ```bash
   cd svelte-todo
   ```
2. Install the necessary dependencies (Node.js is required):
   ```bash
   npm install
   ```
3. Start the local development server:
   ```bash
   npm run dev
   ```
4. Open your web browser and visit `http://localhost:5173`.

## 🧠 Core Concepts Learned

This project demonstrates the core pillars of Svelte 5:

* **State Management (Runes):** Using `$state()` to declare variables that automatically update the screen when their data changes (similar to Global Variables in App Inventor).
* **Two-Way Data Binding:** Using `bind:value` on text inputs and `bind:checked` on checkboxes to keep the HTML and the JavaScript perfectly in sync without writing manual update functions.
* **Event Handling:** Using standard HTML events like `onsubmit` and `onclick` to trigger functions (similar to "When Button.Click" blocks).
* **TypeScript Integration:** Using `<script lang="ts">` to define explicit types for our variables and function parameters, helping the IDE catch errors before the code even runs.
* **Accessibility (a11y):** Ensuring UI elements like icon-only buttons have proper `aria-label` attributes so they are usable by screen readers.

## 📁 File Structure

The main logic and styling for this app are located in:
* `svelte-todo/src/App.svelte` - Contains the HTML, TypeScript logic, and component structure.
* `svelte-todo/src/app.css` - Contains the modern, glassmorphism-inspired CSS styling.

---
*Happy Coding! ✨*

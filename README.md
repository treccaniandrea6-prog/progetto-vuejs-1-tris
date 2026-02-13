# Progetto Vue.js 1 – Tic Tac Toe (Tris)

Interactive implementation of the classic Tic Tac Toe game built with **Vue.js 3** using the Composition API.

Live Demo:  
👉 https://progetto-vuejs-1-tris.netlify.app

GitHub Repository:  
👉 https://github.com/treccaniandrea6-prog/progetto-vuejs-1-tris

---

## Project Overview

This project is a fully interactive web version of the classic 3x3 Tic Tac Toe game.

Two players alternate turns (X and O).  
The application automatically:

- Detects winning combinations
- Detects draw scenarios
- Prevents invalid moves
- Allows full game reset

The interface updates reactively without page reloads, ensuring a smooth user experience.

---

## Technologies Used

- Vue.js 3
- Composition API
- Vite
- Reactive state management (`ref`, `computed`)
- Netlify (Deployment)

---

## Technical Implementation

### State Management

The game state is handled using Vue’s reactivity system:

- `ref` for board state and player turn
- `computed` for dynamic game status
- Winner detection through predefined winning combinations

### Game Logic

- 9-cell reactive board array
- Turn alternation logic (X / O)
- Win condition check after each move
- Draw detection when the board is full
- Disabled cells after game completion

### UI Structure

- Grid layout using CSS Grid
- Scoped component styling
- Clean separation between logic and presentation

---

## Installation & Local Development

Clone the repository:

git clone https://github.com/treccaniandrea6-prog/progetto-vuejs-1-tris.git

Navigate into the project:

cd progetto-vuejs-1-tris

Install dependencies:

npm install

Start development server:

npm run dev

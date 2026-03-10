# Progetto Vue.js 1 – Tic Tac Toe (Tris)

Interactive implementation of the classic Tic Tac Toe game built with **Vue.js 3** using the Composition API.

Live Demo:  
👉 https://progetto-vuejs-1-tris.netlify.app

GitHub Repository:  
👉 https://github.com/treccaniandrea6-prog/progetto-vuejs-1-tris

---

## Project Overview

This project is a fully interactive web implementation of the classic **3x3 Tic Tac Toe game** built with **Vue.js 3**.

Two players alternate turns (X and O) while the application manages the game state reactively. The interface updates instantly without page reloads thanks to Vue's reactivity system.

The application automatically:

- Detects winning combinations
- Detects draw scenarios
- Prevents invalid moves
- Disables cells when the game ends
- Allows the game to be fully reset

---

## Technologies Used

- Vue.js 3
- Composition API
- Vite
- Reactive state management (`ref`, `computed`)
- CSS Grid
- Netlify (Deployment)

---

## Technical Implementation

### Reactive State Management

The game state is managed using Vue's reactivity system:

- `ref()` is used to manage:
  - the game board
  - the current player
  - the winner

- `computed()` is used to derive:
  - the current game status
  - draw detection

This approach ensures that the UI automatically updates whenever the state changes.

---

### Game Logic

The core game logic includes:

- A reactive **9-cell board array**
- Turn alternation between **X and O**
- Winner detection through predefined **winning combinations**
- Draw detection when the board is completely filled
- Blocking invalid moves on occupied cells
- Preventing moves after the game ends

---

### Component Architecture

The project was refactored to follow a **component-based architecture**, improving readability and maintainability.

Components used:

- **GameBoard.vue**  
  Responsible for rendering the 3×3 grid and managing cell interactions.

- **GameCell.vue**  
  Represents a single cell of the board and handles click interactions and visual feedback.

- **GameStatus.vue**  
  Displays the current game status (next player, winner, or draw).

The main game logic remains inside **App.vue**, which manages the global game state.

---

### UI Improvements

The interface includes several visual enhancements:

- Color distinction between **X and O**
- Hover effects for interactive cells
- Highlighting of the **winning combination**
- Clean layout using **CSS Grid**
- Centered layout for better user experience

---

## Installation & Local Development

Clone the repository:

    git clone https://github.com/treccaniandrea6-prog/progetto-vuejs-1-tris.git

Navigate into the project folder:

    cd progetto-vuejs-1-tris

Install dependencies:

    npm install

Start the development server:

    npm run dev

---

## Deployment

The project is deployed on **Netlify**.

Each push to the repository triggers a new deployment, allowing quick updates and easy project sharing.

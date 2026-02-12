<script setup>
import { ref, computed } from "vue";

const board = ref(Array(9).fill(null)); // 9 celle: null | "X" | "O"
const xIsNext = ref(true); // true = X, false = O
const winner = ref(null); // "X" | "O" | null

const winningCombinations = [
  [0, 1, 2],
  [3, 4, 5],
  [6, 7, 8],
  [0, 3, 6],
  [1, 4, 7],
  [2, 5, 8],
  [0, 4, 8],
  [2, 4, 6],
];

const isDraw = computed(() => {
  return !winner.value && board.value.every((cell) => cell !== null);
});

const status = computed(() => {
  if (winner.value) return `Winner: ${winner.value}`;
  if (isDraw.value) return "Draw!";
  return `Next player: ${xIsNext.value ? "X" : "O"}`;
});

function checkWinner() {
  for (const [a, b, c] of winningCombinations) {
    const v = board.value[a];
    if (v && v === board.value[b] && v === board.value[c]) {
      winner.value = v;
      return;
    }
  }
}

function handleClick(index) {
  // blocca click se: cella già piena, c'è un vincitore, o è pareggio
  if (board.value[index] || winner.value || isDraw.value) return;

  const newBoard = [...board.value];
  newBoard[index] = xIsNext.value ? "X" : "O";
  board.value = newBoard;

  checkWinner();

  // cambia turno SOLO se non c'è un vincitore
  if (!winner.value) {
    xIsNext.value = !xIsNext.value;
  }
}

function resetGame() {
  board.value = Array(9).fill(null);
  xIsNext.value = true;
  winner.value = null;
}
</script>

<template>
  <div class="container">
    <h1>Tic Tac Toe (Tris)</h1>
    <p class="status">{{ status }}</p>

    <div class="board">
      <button
        v-for="(cell, index) in board"
        :key="index"
        class="cell"
        :disabled="!!cell || !!winner || isDraw"
        @click="handleClick(index)"
      >
        {{ cell }}
      </button>
    </div>

    <button class="reset" @click="resetGame">Reset Game</button>
  </div>
</template>

<style scoped>
.container {
  text-align: center;
  font-family: Arial, sans-serif;
  padding: 40px;
}

.board {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  gap: 10px;
  justify-content: center;
  margin: 20px 0;
}

.cell {
  width: 100px;
  height: 100px;
  font-size: 32px;
  font-weight: bold;
  cursor: pointer;
}

.cell:disabled {
  cursor: not-allowed;
  opacity: 0.9;
}

.status {
  font-size: 20px;
  margin-bottom: 10px;
}

.reset {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
</style>

<script setup>
import { ref, computed } from "vue";
import GameBoard from "./components/GameBoard.vue";
import GameStatus from "./components/GameStatus.vue";

const board = ref(Array(9).fill(null));
const xIsNext = ref(true);
const winner = ref(null);
const winningCells = ref([]);

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
      winningCells.value = [a, b, c];
      return;
    }
  }
}

function handleClick(index) {
  if (board.value[index] || winner.value || isDraw.value) return;

  const newBoard = [...board.value];
  newBoard[index] = xIsNext.value ? "X" : "O";
  board.value = newBoard;

  checkWinner();

  if (!winner.value) {
    xIsNext.value = !xIsNext.value;
  }
}

function resetGame() {
  board.value = Array(9).fill(null);
  xIsNext.value = true;
  winner.value = null;
  winningCells.value = [];
}
</script>

<template>
  <div class="container">
    <h1>Tic Tac Toe (Tris)</h1>

    <GameStatus :status="status" :winner="winner" :isDraw="isDraw" />

    <GameBoard
      :board="board"
      :winner="winner"
      :isDraw="isDraw"
      :winningCells="winningCells"
      @cell-click="handleClick"
    />

    <button class="reset" @click="resetGame">Reset Game</button>
  </div>
</template>

<style scoped>
.container {
  text-align: center;
  font-family: Arial, sans-serif;
  padding: 40px;
  min-height: 100vh;
  background: #f4f6f8;
}

h1 {
  margin-bottom: 16px;
}

.reset {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  border: none;
  border-radius: 8px;
  background: #222;
  color: white;
}

.reset:hover {
  opacity: 0.9;
}
</style>
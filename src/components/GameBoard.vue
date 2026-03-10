<script setup>
import GameCell from "./GameCell.vue";

defineProps({
  board: {
    type: Array,
    required: true,
  },
  winner: {
    type: String,
    default: null,
  },
  isDraw: {
    type: Boolean,
    required: true,
  },
  winningCells: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits(["cell-click"]);
</script>

<template>
  <div class="board">
    <GameCell
      v-for="(cell, index) in board"
      :key="index"
      :value="cell"
      :disabled="!!cell || !!winner || isDraw"
      :isWinningCell="winningCells.includes(index)"
      @click="emit('cell-click', index)"
    />
  </div>
</template>

<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  gap: 10px;
  justify-content: center;
  margin: 20px 0;
}
</style>
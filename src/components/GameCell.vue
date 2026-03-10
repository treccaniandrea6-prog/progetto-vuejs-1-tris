<script setup>
defineProps({
  value: {
    type: String,
    default: null,
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  isWinningCell: {
    type: Boolean,
    default: false,
  },
});

defineEmits(["click"]);
</script>

<template>
  <button
    class="cell"
    :class="[
      value === 'X' ? 'x' : '',
      value === 'O' ? 'o' : '',
      isWinningCell ? 'winner-cell' : ''
    ]"
    :disabled="disabled"
    @click="$emit('click')"
  >
    {{ value }}
  </button>
</template>

<style scoped>
.cell {
  width: 100px;
  height: 100px;
  font-size: 32px;
  font-weight: bold;
  cursor: pointer;
  border: none;
  border-radius: 12px;
  background: white;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  transition: transform 0.15s ease, background 0.2s ease;
}

.cell:hover:enabled {
  transform: scale(1.04);
  background: #f0f0f0;
}

.cell:disabled {
  cursor: not-allowed;
  opacity: 0.95;
}

.x {
  color: #d62828;
}

.o {
  color: #1d4ed8;
}

.winner-cell {
  background: #ffe082;
}
</style>
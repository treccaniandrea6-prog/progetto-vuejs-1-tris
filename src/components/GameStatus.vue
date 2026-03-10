<script setup>
defineProps({
  status: {
    type: String,
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
});
</script>

<template>
  <p
    class="status"
    :class="{
      'winner-text': winner,
      'draw-text': isDraw
    }"
  >
    {{ status }}
  </p>
</template>

<style scoped>
.status {
  font-size: 20px;
  margin-bottom: 10px;
  font-weight: bold;
}

.winner-text {
  color: #15803d;
}

.draw-text {
  color: #b45309;
}
</style>
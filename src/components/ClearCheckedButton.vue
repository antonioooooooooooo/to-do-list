<script setup>
</script>

<template>
  <button
    @click="$emit('clear-checked')"
    class="clear-checked-button"
  >Clear Checked</button>
</template>

<style scoped>
.clear-checked-button {
  background-color: #e0462b;
  cursor: pointer;
  border-radius: 20px;
  height: 30px;
  width: 120px;
  border: none;
  transition: background-color 0.1s ease-in;
  color: white;
  font-weight: 700;
  margin-top: 40px;
}
.clear-checked-button:active {
  outline: none;
}
.clear-checked-button:hover,
.clear-checked-button:focus {
  background-color: #e0872b;
}
</style>
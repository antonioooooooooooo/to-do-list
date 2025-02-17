<script setup>
import { ref } from "vue";

const currInput = ref("");

defineEmits(["add-task"]);
</script>

<template>
  <div class="input-bar-wrapper">
    <input
      v-model="currInput"
      class="input-bar"
      type="text"
    />
    <button
      @click="() => {$emit('add-task', currInput); currInput = ''}"
      class="add-button"
    >Add</button>
  </div>
</template>

<style scoped>
.input-bar-wrapper {
  display: flex;
  gap: 8px;
  height: 40px;
  align-items: center;
  margin-bottom: 20px;
}
.input-bar {
  height: 100%;
  width: 400px;
  border-radius: 20px;
  border: none;
  background-color: #dbdbdb;
  padding-left: 12px;
  padding-right: 70px;
  font-family: "Open Sans";
}
.input-bar:focus {
  outline: none;
}
.add-button {
  height: 30px;
  width: 60px;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  background-color: #7534e1;
  transition: background-color 0.1s ease-in;
  color: white;
  font-weight: 700;
  margin-left: -74px;
}
.add-button:hover,
.add-button:focus {
  background-color: #c434e1;
}
</style>
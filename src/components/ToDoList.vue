<script setup>
import Task from "./Task.vue";
import InputBar from "./InputBar.vue";
import ClearCheckedButton from "./ClearCheckedButton.vue";
import { ref } from "vue";

const tasks = ref([]);
const checked = ref([]);

function addNewTask(task) {
  tasks.value = [...tasks.value, task];
  checked.value.push(false);
}

function removeTask(index) {
  tasks.value.splice(index, 1);
  checked.value.splice(index, 1);
}

function toggleChecked(index) {
  checked.value[index] = !checked.value[index];
}

function clearAllChecked() {
  let count = 0;
  let newTasks = [];

  for (const [index, val] of checked.value.entries()) {
    if (!val) {
      newTasks.push(tasks.value[index]);
      count++;
    }
  }

  tasks.value = newTasks;
  checked.value = Array(count).fill(false);
}
</script>

<template>
  <div class="to-do-list-wrapper">
    <img
      class="lana-image"
      src="https://preview.redd.it/c5oh1izzzwu61.jpg?width=1080&crop=smart&auto=webp&s=8ce3c5954549795e4ba992d4603efdb5aea89875"
    />
    <h1 class="to-do-list-title">Anton's To-Do List</h1>
    <InputBar @add-task="addNewTask" />
    <Task
      v-for="(task, index) of tasks"
      :key="index"
      :title="task"
      :isChecked="checked[index]"
      @toggle-checked="() => toggleChecked(index)"
      @remove-task="() => removeTask(index)"
    />
    <ClearCheckedButton
      v-if="tasks.length > 0"
      @clear-checked="clearAllChecked"
    />
  </div>
</template>

<style scoped>
.lana-image {
  height: 275px;
  margin-bottom: 40px;
  border-radius: 20px;
  border: 1px solid black;
}
.to-do-list-title {
  text-align: center;
  font-weight: 700;
  text-decoration: underline;
  text-underline-offset: 6px;
  margin-bottom: 40px;
}
.to-do-list-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}
</style>
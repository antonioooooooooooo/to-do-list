<script setup>
defineProps({
  title: String,
  isChecked: Boolean,
});
</script> 

<template>
  <div class="task-wrapper">
    <input
      @click="$emit('toggle-checked')"
      type="checkbox"
      class="task-checkbox"
      :checked="isChecked"
    />
    <div
      class="task-title"
      :class="{'checked-task-title': isChecked}"
    >{{ title }}</div>
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Red_X.svg/1200px-Red_X.svg.png"
      @click="$emit('remove-task')"
      class="x-button"
    />
  </div>
</template>

<style scoped>
.task-wrapper {
  display: flex;
  align-items: center;
}
.task-checkbox {
  width: 18px;
  height: 18px;
  margin-right: 8px;
  background-color: white;
  border-radius: 50%;
  vertical-align: middle;
  border: 1px solid #ddd;
  appearance: none;
  -webkit-appearance: none;
  outline: none;
  cursor: pointer;
  position: relative;
}
.task-checkbox:checked::before {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  width: 8px;
  height: 8px;
  background-color: turquoise;
  border-radius: 50%;
  transform: translate(-50%, -50%);
}
.task-title {
  margin-right: 8px;
}
.checked-task-title {
  text-decoration: line-through;
}
.x-button {
  height: 14px;
  width: 14px;
  cursor: pointer;
}
</style>
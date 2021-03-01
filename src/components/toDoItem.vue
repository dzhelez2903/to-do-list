<template>
  <li>
    <span v-bind:class="{task_done: task.completed}">
      <input type="checkbox" v-on:change="task.completed=!task.completed">
      {{ index+1 }}
      {{ task.title }}
    </span>
    <button class="btn" v-on:click="$emit('delete-task', task.id)">
      &times;</button>
  </li>
</template>

<script>
export default {
  name: "toDoItem",
  props: {
    task: {
      Object,
      required: true
    },
    index: Number
  }
}
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 20px;
    margin-bottom: 10px;
    font-size: 20px;
  }

  input {
    margin-right: 15px;
  }

  .btn {
    background-color: #e52626;
    font-size: 30px;
    font-weight: bold;
    color: #fff;
    line-height: 0;
    padding: 16px 8px;
    border-color: transparent;
    border-radius: 50%;
    cursor: pointer;
    transition: 0.3s;
  }

  .btn:hover {
    background-color: transparent;
    color: #e52626;
    border-color: #e52626;
  }

  .task_done {
    text-decoration: line-through;
  }
</style>
<template>
  <div>
    <ul>
      <toDoItem
      v-for="(task,n) of tasks"
      v-bind:task="task"
      v-bind:index="n"
      v-on:delete-task="del"
      />
    </ul>
  </div>
</template>

<script>
import toDoItem from "@/components/toDoItem";
export default {
  props: [
     'tasks'
  ],
  components: {
    toDoItem
  },
  methods: {
    del(id) {
      this.$emit('del-item', id)
    }
  }
}
</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>
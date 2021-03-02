<template>
  <div id="app">
    <h1>Todo Application</h1>
    <addItem
      @addItem="addItem"
    />
    <hr>
    <toDoList
        v-bind:tasks="tasks"
        @del-item="delItem"
    />
  </div>
</template>

<script>
import toDoList from '@/components/toDoList';
import addItem from "@/components/addItem";
export default {
  name: 'App',
  data() {
    return {
      tasks: []
    }
  },

  methods: {
    delItem(id) {
      this.tasks = this.tasks.filter(t=>t.id!==id)
    },
    addItem(newToDo) {
      this.tasks.push(newToDo)
    }
  },

  components: {
    toDoList,
    addItem
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  max-width: 1600px;
  margin: 0 auto;
  padding-top: 60px;
  background: radial-gradient(circle, rgba(210,210,223,1) 0%, rgba(243,243,246,1) 50%, rgba(255,255,255,1) 100%, rgba(255,255,255,1) 100%);

  hr {
    margin: 50px 0;
    border: none;
    height: 2px;
    color: #b6b4d7;
    background-color: #b6b4d7;
  }
}
</style>

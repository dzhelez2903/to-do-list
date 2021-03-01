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
      tasks: [
        /*{id: 1, title: 'купить хлеб', completed: false},
        {id: 2, title: 'купить мыло', completed: false},
        {id: 3, title: 'купить пиво', completed: false}*/
      ]
    }
  },

  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(response => response.json())
        .then(json => {
          this.tasks = json
        })
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
  margin-top: 60px;
}

 hr {
   margin: 50px 0;
 }
</style>

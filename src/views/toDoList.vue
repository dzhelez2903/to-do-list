<template>
  <div>
    <router-link to="/">Home</router-link>
    <hr>
    <addItem
        @addItem="addItem"
    />
    <hr>
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not_completed">Not completed</option>
    </select>
    <toDoList
        v-if="filteredTasks.length"
        v-bind:tasks="filteredTasks"
        @del-item="delItem"
    />
    <p v-else>
      Add something!!!
    </p>
  </div>
</template>

<script>
import toDoList from '@/components/toDoList';
import addItem from "@/components/addItem";
export default {
  name: 'App',
  data() {
    return {
      tasks: [],
      filter: 'all'
    }
  },
  computed: {
    filteredTasks() {
     if (this.filter === 'all') {
       return this.tasks
     }

     if (this.filter === 'completed') {
       return this.tasks.filter(t => t.completed)
     }

      if (this.filter === 'not_completed') {
        return this.tasks.filter(t => !t.completed)
      }
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
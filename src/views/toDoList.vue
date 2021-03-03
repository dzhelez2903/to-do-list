<template>
  <div>
    <router-link to="/">Home</router-link>

    <addItem @addItem="addItem"/>
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
    <hr>
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

<style lang="scss" scoped>

a {
  text-decoration: none;
  color: #151414;
  font-size: 25px;

  &:hover {
    text-shadow: 1px 1px 10px rgba(9, 141, 242, 0.48);
  }
}

select {
  width: 30%;
  font-size: 20px;
  margin-bottom: 50px;
  outline:none;
  border: 1px solid #b6b4d7;
  border-radius: 5px;
  opacity: 0.7;

  &:focus {
    box-shadow: inset 1px 0 10px 0 rgba(182, 180, 215, 0.48);
  }
}

p {
  font-size: 25px;
}
</style>
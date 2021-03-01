<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Add task</button>
  </form>
</template>

<script>
export default {
name: "addItem",
  data() {
  return {
    title: ''
  }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newToDo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('addItem', newToDo)
        this.title=''
      }
    }
  }
}
</script>

<style scoped>

  form {
    margin: 50px auto 0;
  }
  input {
    width: 30%;
    margin-right: 20px;
  }
</style>
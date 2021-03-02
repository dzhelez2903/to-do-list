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

<style lang="scss" scoped>

  form {
    margin: 50px auto 0;

    input {
      width: 30%;
      margin-right: 20px;
      font-size: 20px;
      outline:none;
      border: 1px solid #b6b4d7;
      border-radius: 5px;
      opacity: 0.7;

      &:focus {
        box-shadow: inset 1px 0 10px 0 rgba(182, 180, 215, 0.48);
      }
    }

    button {
      font-size: 18px;
      color: #fff;
      border-color: transparent;
      border-radius: 5px;
      padding: 3px 10px;
      background-color: #b6b4d7;
      cursor: pointer;
      transition: 0.3s;
      outline: none;
      text-transform: uppercase;

      &:hover {
        border-color: #b6b4d7;
        color: #b6b4d7;
        background-color: transparent;
        box-shadow: 1px 0 10px 0 rgba(182, 180, 215, 0.48);
      }
    }
  }

</style>
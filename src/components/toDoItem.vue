<template>
  <li>
    <div class="grid-container">
      <div class="check">
        <label>
          <input class="checkbox" type="checkbox" v-on:change="task.completed=!task.completed">
          <span>
            <font-awesome-icon icon="check"/>
          </span>
        </label>
      </div>
      <div class="title">
        <p v-bind:class="{task_done: task.completed}">
          {{ index+1 }}
          {{ task.title | upp}}
        </p>
      </div>
      <div class="button">
        <a class="btn" v-on:click="$emit('delete-task', task.id)"><font-awesome-icon icon="trash-alt" /></a>
      </div>
    </div>
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
  },
  filters: {
    upp(value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style lang="scss" scoped>
.grid-container {
  max-width: 1600px;
  display: grid;
  grid-template-columns: 50px auto 50px;
  grid-template-rows: auto;
  gap: 0 0;
  grid-template-areas:
    "check title button";
  border: 1px solid #b6b4d7;
  border-radius: 5px;
  margin-bottom: 20px;

  &:hover {
    box-shadow: 1px 0 10px 0 rgba(182, 180, 215, 0.48);
  }

  .check {
    grid-area: check;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;

    label {
      width: 22px;
      height: 18px;
      display: block;
      position: absolute;
    }

    input {
      display: none;

      &:checked+span .fa-check {
        color: green;
      }
    }

    span {
      position: absolute;
      left: -2px;
    }

    input+span {
      position: absolute;
      width: 100%;
      height: 100%;
      cursor: pointer;
    }

    .fa-check {
      color: #b6b4d7;
      font-size: 20px;
    }

  }
  .title {
    grid-area: title;
    display: flex;
    justify-content: flex-start;
    flex-wrap: wrap;
    align-items: center;
  }
  .button {
    grid-area: button;
    display: flex;
    justify-content: center;
    align-items: center;

    a{
      cursor: pointer;

      .fa-trash-alt {
        color: #b6b4d7;
        font-size: 20px;
        transition: 0.3s;

        &:hover {
          color: #820404;
        }
      }
    }

  }

  .task_done {
    text-decoration: line-through;
  }
}

</style>
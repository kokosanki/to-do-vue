<template>
  <div class="todo">
    <div class="todo_text" :class="[isActive ? 'isDone' : null]">
      <li class="todo_item">
        {{ todo.text }}
      </li>
    </div>
    <div class="todo_buttons">
      <button v-on:click="$emit('remove-todo', todo)">Delete</button>
      <button
        v-on:click="
          $emit('complete-todo', todo);
          completeTodo();
        "
      >
        Done
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["todo"],
  data() {
    return {
      isActive: false
    };
  },
  methods: {
    completeTodo() {
      this.isActive = true;
    }
  }
};
</script>

<style scoped lang="scss">
.todo {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  margin-top: 5px;
  &_text {
    width: 80vw;
    box-sizing: border-box;
    border-top: 2px solid #108d8f;
    border-bottom: 2px solid #108d8f;
    padding: 5px 2.5px;
  }
  &_buttons {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    button {
      width: 60px;
      height: 30px;
      color: #fff;
      background-color: #108d8f;
      font-weight: bold;
      border: none;
      border-radius: 5px;
      margin: 5px;
      &:hover {
        cursor: pointer;
      }
      &:active {
        color: #108d8f;
        border: 2px solid #108d8f;
        border-radius: 5px;
        background-color: #fff;
      }
      &:focus {
        outline: none;
      }
    }
  }
}

.isDone {
  background-color: #c7c9c9;
}

@media (min-width: 800px) {
  .todo {
    flex-direction: row;
    &_text {
      width: 100%;
    }
    &_buttons {
      width: auto;
    }
  }
}
</style>

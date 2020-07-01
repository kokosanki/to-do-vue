<template>
  <div>
    <form action v-on:submit="addTodo" class="form">
      <input
        type="text"
        placeholder="What do you have to do?"
        v-model="newTodo"
        class="form_input"
      />
      <input
        v-on:submit.prevent
        type="submit"
        value="Submit"
        class="form_button"
      />
    </form>
  </div>
</template>

<script>
import { uuid } from "vue-uuid";

export default {
  props: ["todos"],
  data() {
    return {
      newTodo: ""
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length > 0) {
        const id = uuid.v4();
        const task = this.newTodo;
        this.todos.push({ text: task, id: id });
        this.newTodo = "";
      } else {
        alert("Write a todo!");
      }
    }
  }
};
</script>
<style scoped lang="scss">
.form {
  white-space: nowrap;
  &_input {
    border: 2px solid #108d8f;
    height: 30px;
    box-sizing: border-box;
    width: 60vw;
    &:focus {
      outline: none;
    }
  }
  &_button {
    width: 60px;
    height: 30px;
    color: #fff;
    background-color: #108d8f;
    font-weight: bold;
    border: none;
    &:hover {
      cursor: pointer;
    }
    &:active {
      color: #108d8f;
      border: 2px solid #108d8f;
      background-color: #fff;
    }
    &:focus {
      outline: none;
    }
  }
}
</style>

<template>
  <div class="home">
    <h1>Let's do this Vue!</h1>
    <AddTodo :todos="todos" />
    <ol>
      <Todo
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        v-on:remove-todo="onRemoveTodo"
        v-on:complete-todo="onCompleteTodo"
      ></Todo>
    </ol>
  </div>
</template>

<script>
import AddTodo from "@/components/AddTodo.vue";
import Todo from "@/components/Todo.vue";

export default {
  name: "Home",
  components: { AddTodo, Todo },
  props: ["done", "onCompleteTodo"],
  data() {
    return {
      todos: [],
      postFontSize: 1
    };
  },
  methods: {
    onRemoveTodo(todo) {
      this.todos.splice(this.todos.indexOf(todo), 1);
    }
  }
};
</script>
<style lang="scss" scoped>
.home {
  ol {
    padding: 0;
  }
}
@media (min-width: 800px) {
  .home {
    ol {
      padding-left: 30px;
    }
  }
}
</style>

<template>
  <div>
    <h2>Done Todos</h2>
    <ol>
      <li class="todo" v-for="todo in done" :key="todo.id">{{ todo.text }}</li>
    </ol>
  </div>
</template>

<script>
export default {
  props: ["done"]
};
</script>

<style lang="scss" scoped>
.todo {
  margin-top: 5px;
  box-sizing: border-box;
  border-top: 2px solid #108d8f;
  border-bottom: 2px solid #108d8f;
  padding: 5px 2.5px;
}
@media (max-width: 800px) {
  ol {
    padding: 0;
  }
}
</style>

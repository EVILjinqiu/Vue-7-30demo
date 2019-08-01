<template>
  <ul class="todo-main">
    <Item v-for="(todo, index) in todos" :key="todo.id" :todo="todo"
    :deleteTodo="deleteTodo" :index="index" :updateTodo="updateTodo"/>
  </ul>
</template>

<script>
import Item from "./Item";
export default {
  props: ['todos','deleteTodo', 'updateTodo'],
  components: {
    Item
  }
};
</script>

<style scoped>
</style>

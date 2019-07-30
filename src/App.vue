<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <Header :addTodo="addTodo"></Header>
      <List :todos="todos" :deleteTodo="deleteTodo"></List>
      <Footer></Footer>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import List from "./components/List";
import Footer from "./components/Footer";

export default {
  data() {
    return {
      todos: [
        { id: 1, title: "AAA", complete: false },
        { id: 4, title: "AAA", complete: true },
        { id: 7, title: "AAA", complete: false },
      ]
    };
  },

  methods: {
    addTodo (todo) {
      this.todos.unshift(todo)
    },
    deleteTodo (index) {
      this.todos.splice(index, 1)
    }
  },
  components: {
    Header,
    List,
    Footer
  }
};
</script>
<style>
</style>


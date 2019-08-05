<template>
  <div id="app">
    <Todos :todos="todos" @addTodo="addTodo" @deleteTodo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import axios from "axios";

export default {
  name: "app",
  components: {
    Todos
  },
  data() {
    return {
      message: "Hello World!",
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => {
        return todo.id != id;
      });
    },
    addTodo(newTodo) {
      newTodo.desc = "Created at 12/22/2019";
      this.todos = [...this.todos, newTodo];
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => {
        this.todos = res.data;
      });
  }
};
</script>
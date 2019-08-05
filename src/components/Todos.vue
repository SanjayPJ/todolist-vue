<template>
  <div class="container">
    <Header />
    <div class="card mt-2 bg-light">
      <div class="card-body">
        <div class="form-group">
          <input
            type="text"
            class="form-control"
            id="exampleFormControlInput1"
            placeholder="Search Todos"
          />
        </div>
        <div class="form-group form-check m-0">
          <input type="checkbox" class="form-check-input" id="exampleCheck1" />
          <label class="form-check-label" for="exampleCheck1">Show completed todos</label>
        </div>
      </div>
    </div>
    <div class="card bg-light mt-2">
      <div class="card-body">
        <div :key="todo.id" v-for="todo in todos">
          <TodoItem @deleteTodo="passDeleteTodo" :todo="todo" />
        </div>
      </div>
    </div>
    <AddTodo @addTodo="passAddTodo" />
  </div>
</template>

<script>
import TodoItem from "./TodoItem";
import AddTodo from "./AddTodo";
import Header from "./Header";
export default {
  name: "Todos",
  components: {
    TodoItem,
    AddTodo,
    Header
  },
  props: ["todos"],
  methods: {
    passDeleteTodo(id) {
      this.$emit("deleteTodo", id);
    },
    passAddTodo(newTodo) {
      this.$emit("addTodo", newTodo);
    }
  }
};
</script>

<style scoped>
</style>

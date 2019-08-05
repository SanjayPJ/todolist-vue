<template>
  <div class="card bg-light mt-2">
    <div class="card-body">
      <form @submit.prevent="addTodo">
        <div class="form-group">
          <input type="text" v-model="title" class="form-control" id="exampleFormControlInput1" />
        </div>
        <button type="submit" class="btn btn-primary w-100">Add Todo</button>
      </form>
    </div>
  </div>
</template>

<script>
import uuid from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      };
      this.$emit("addTodo", newTodo);
      this.title = "";
    }
  }
};
</script>

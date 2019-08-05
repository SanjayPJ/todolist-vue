<template>
  <div class="todo-item" :class="{'is-complete': todo.completed}">
    <div class="row py-3">
      <div class="col-11">
        <div class="form-check">
          <input
            class="form-check-input"
            @click="markComplete"
            v-model="todo.completed"
            type="checkbox"
            id="gridCheck"
          />
          <label
            class="form-check-label ml-2"
            :class="{'strike text-muted': todo.completed}"
            for="gridCheck"
          >
            {{ todo.title }}
            <br />
            <small class="text-muted">{{ todo.desc}}</small>
          </label>
        </div>
      </div>
      <div class="col-1">
        <button
          @click="$emit('deleteTodo', todo.id)"
          type="button"
          class="close"
          aria-label="Close"
        >
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.strike {
  text-decoration: line-through;
}
</style>


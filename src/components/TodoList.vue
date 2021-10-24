<template>
  <div :class="$style.container">
    <Todo
      :todos="todos"
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @delete-todo="$emit('delete-todo', todo.id)"
      @toggle-finished="$emit('toggle-finished', todo.id)"
    />
  </div>
</template>

<script>
import Todo from "./Todo";
export default {
  name: "TodoList",
  components: { Todo },
  props: {
    todos: Array,
  },
  emits: ["delete-todo", "toggle-finished"],
};
</script>

<style module lang="scss">
.container {
  width: 100%;
  background-color: #25273d;
  margin-top: 4rem;
  box-shadow: 0px 35px 50px -15px rgba(0, 0, 0, 0.5);
  border-radius: 5px;
}
</style>

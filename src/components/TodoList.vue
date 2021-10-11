<template>
  <div :class="$style.container">
    <Todo
      :todos="todos"
      v-for="(todo, index) in todos"
      :key="todo.id"
      @remove="removeTask(index)"
      :todo="todo"
    />
  </div>
</template>

<script>
import Todo from './Todo';
export default {
  name: 'TodoList',
  components: { Todo },
  props: {
    todos: Array,
  },
  methods: {
    removeTask(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style module lang="scss">
.container {
  width: 100%;
  height: 50vh;
  background-color: #25273d;
  margin-top: 4rem;
  box-shadow: 0px 35px 50px -15px rgba(0, 0, 0, 0.5);
  border-radius: 5px;
}
</style>

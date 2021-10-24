<template>
  <form @submit.prevent="addTodo" :class="$style.form">
    <div :class="$style.input_container">
      <input v-model="task" type="text" placeholder="Create a new todo..." />
    </div>
  </form>
  <TodoList
    @delete-todo="deleteTodo"
    @toggle-finished="toggleFinished"
    :todos="todos"
  />
  <TodoFilter :todos="todos" />
</template>

<script>
import TodoList from "./TodoList";
import TodoFilter from "./TodoFilter.vue";

export default {
  name: "Form",
  components: {
    TodoList,
    TodoFilter,
  },
  data() {
    return {
      task: "",
      todos: [],
      id: 1,
    };
  },
  methods: {
    addTodo() {
      if (!this.task) {
        alert("Please type a todo");
        return;
      }

      this.todos = [
        ...this.todos,
        {
          id: Math.floor(Math.random() * 100000),
          isFinished: false,
          task: this.task,
        },
      ];

      this.task = "";
    },
    toggleFinished(id) {
      this.todos.map((todo) =>
        todo.id === id ? (todo.isFinished = !todo.isFinished) : todo
      );
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
  },
};
</script>

<style module lang="scss">
.form {
  margin-top: 5rem;
}

.input_container {
  input {
    background-color: #25273d;
    box-shadow: 0px 35px 50px -15px rgba(0, 0, 0, 0.5);
    border-radius: 5px;
    border: none;
    width: 100%;
    outline: none;
    padding: 2rem;
    color: #c8cbe7;
    font-size: 1.8rem;

    &::placeholder {
      color: #767992;
      font-size: 1.8rem;
    }
  }
}
</style>

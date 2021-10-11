<template>
  <form @submit.prevent="addTodo" :class="$style.form">
    <div :class="$style.input_container">
      <input v-model="task" type="text" placeholder="Create a new todo..." />
    </div>
  </form>
  <TodoList :todos="todos" />
</template>

<script>
import TodoList from './TodoList';
export default {
  name: 'Form',
  components: { TodoList },
  data() {
    return {
      task: '',
      todos: [],
      id: 1,
    };
  },
  methods: {
    addTodo() {
      if (this.task.length === 0) return;
      this.todos.push({
        id: this.id++,
        task: this.task,
        isFinished: false,
      });

      this.task = '';
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

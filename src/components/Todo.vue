<template>
  <div
    :class="[
      $style.todo_container,
      !todo.isFinished ? $style.not_finished : null,
    ]"
  >
    <div :class="$style.checked" @click="$emit('toggle-finished', todo.id)">
      <div :class="$style.circle">
        <img src="../assets/icon-check.svg" alt="check" />
      </div>
    </div>
    <div :class="$style.todo_task">
      <span :class="$style.todo_task__text">{{ todo.task }}</span>
    </div>

    <div :class="$style.cross" @click="$emit('delete-todo', todo.id)" />
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: {
    todos: Array,
    todo: Object,
  },
  methods: {
    toggleFinished() {
      this.todo.isFinished = !this.todo.isFinished;
    },
  },
};
</script>

<style module lang="scss">
.todo_container {
  width: 100%;
  height: 9vh;
  display: flex;
  padding: 2rem 0;
  cursor: pointer;
  border-bottom: 1px solid #393a4b;

  .cross {
    height: 100%;
    width: 7rem;
    background-image: url("../assets/icon-cross.svg");
    background-position: center;
    background-repeat: no-repeat;
    display: none;
  }

  &:hover {
    .cross {
      display: block;
    }
  }
}

.checked {
  height: 100%;
  width: 7rem;
  display: flex;
  align-items: center;
  justify-content: center;

  .circle {
    position: relative;
    height: 3rem;
    width: 3rem;
    display: flex;
    position: relative;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    background: linear-gradient(135deg, #55ddff 0%, #c058f3 100%);

    &:hover {
      &::after {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        border-radius: 50px;
        padding: 2px;
        background: linear-gradient(135deg, #55ddff 0%, #c058f3 100%);
        -webkit-mask: linear-gradient(#fff 0 0) content-box,
          linear-gradient(#fff 0 0);
        -webkit-mask-composite: destination-out;
        mask-composite: exclude;
      }
    }
  }
}

.todo_task {
  display: flex;
  align-items: center;
  margin-left: 1rem;
  flex-grow: 1;

  &__text {
    color: #4d5067;
    font-size: 1.8rem;
    text-decoration: line-through;
  }
}

.not_finished {
  .circle {
    border: 1px solid #393a4b;
    background: transparent;

    img {
      display: none;
    }
  }

  .todo_task {
    &__text {
      text-decoration: none;
      color: #c8cbe7;
    }
  }
}
</style>

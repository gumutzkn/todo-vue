<template>
  <div :class="$style.todo_container">
    <div :class="$style.todo_top">
      <h1>TODO</h1>
      <div :class="$style.icon"></div>
    </div>
    <Form />
  </div>
</template>

<script>
import Form from "./Form";
export default {
  name: "TodoContainer",
  components: { Form },
};
</script>

<style module lang="scss">
.todo_container {
  width: 35%;
  min-height: 80vh;
  position: absolute;
  left: 50%;
  top: 10%;
  transform: translateX(-50%);
}

.todo_top {
  display: flex;
  align-items: center;
  justify-content: space-between;

  h1 {
    letter-spacing: 1.5rem;
    font-size: 4rem;
    color: #fff;
  }

  .icon {
    width: 3rem;
    height: 3rem;
    background-image: url("../assets/icon-sun.svg");
    background-size: cover;
    cursor: pointer;
  }
}
</style>

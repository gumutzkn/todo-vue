<template>
  <Banner />
  <TodoContainer />
</template>

<script>
import Banner from "./components/Banner";
import TodoContainer from "./components/TodoContainer";

export default {
  name: "App",
  components: {
    TodoContainer,
    Banner,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@400;700&display=swap");
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
  font-family: "Josefin Sans", sans-serif;
}
body {
  background: #171823;
}
</style>

<template>
  <div :class="$style.container"></div>
</template>

<script>
export default {
  name: "Banner",
};
</script>

<style module lang="scss">
.container {
  width: 100%;
  height: 35rem;
  background-size: cover;
  background-image: url("../assets/bg-desktop-dark.jpg");
}
</style>

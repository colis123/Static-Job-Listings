<template>
  <div class="header"></div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.header {
  height: 9.75rem;
  background: hsl(180, 29%, 50%);
  background-image: url(".././assets/bg-header-desktop.svg");
  background-position: center;
  background-size: cover;
}

@media screen and (max-width: 400px) {
  .header {
    background-image: url(".././assets/bg-header-desktop.svg");
  }
}
</style>

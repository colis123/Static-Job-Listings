<template>
  <div class="header">
    <img
      v-if="window.width < 380"
      src=".././assets/bg-header-mobile.svg"
      alt="Header Background"
    />
    <img
      v-else
      src=".././assets/bg-header-desktop.svg"
      alt="Header Background"
    />
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      window: {
        width: 0,
      },
    };
  },
  created() {
    window.addEventListener("resize", this.handleResize);
  },
  methods: {
    handleResize() {
      this.window.width = window.innerWidth;
    },
  },
};
</script>

<style scoped>
.header {
  height: 9.75rem;
  background: hsl(180, 29%, 50%);
}

@media screen (min-width: 350px) {
}
</style>

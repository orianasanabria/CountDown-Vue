<template>
  <div class="app">
    <Counter />
  </div>
</template>

<script>
import Counter from "@/components/Counter.vue";
export default {
  components: {
    Counter,
  },
};
</script>

<style lang="scss">
html,
body {
  overflow: hidden;
  width: 100vw;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  background-color: #111111;
}
.app {
  display: grid;
  place-items: center;
  font-family: "Poppins", sans-serif;
  height: 100vh;
  display: grid;
  place-items: center;
}
</style>

<template>
  <div id="app">
    <h1 class="title main-title">Vue Todo</h1>
    <ToDo msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import ToDo from "./components/ToDo.vue";

export default {
  name: "App",
  components: {
    ToDo
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.main-title {
  font-size: 24px;
  font-weight: bold;
}
</style>

<template>
  <div id="app">
    <the-home></the-home>
  </div>
</template>

<script>
import TheHome from "./components/TheHome.vue";
export default {
  name: "App",
  components: { TheHome },
};
</script>

<style>
html {
  height: 100vh;
}

body {
  height: 100vh;
  padding: 0;
  margin: 0;
  font-family: "Roboto", sans-serif;
}
</style>

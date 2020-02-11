<template>
  <div id="app">
    <Dashboard></Dashboard>
  </div>
</template>

<script>
//import Elements from "./views/Elements.vue";
import Dashboard from "./views/Dashboard.vue";

export default {
  name: "app",
  components: {
    Dashboard
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: greenyellow;
  margin-top: 0px;
}
</style>

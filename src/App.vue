<template>
  <div id="App"></div>
  <calculator></calculator>
</template>

<script>
import Calculator from "./components/Calculator.vue";

export default {
  name: "App",
  components: {
    Calculator,
  },
};
</script>

<style>
body {
  background: #1e293b;
}
</style>

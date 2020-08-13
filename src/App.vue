<template>
  <div id="app">
    <Counter />
  </div>
</template>

<script>
import Counter from "@/components/Counter";
export default {
  name: "App",
  components: {
    Counter,
  },
};
</script>

<style>
#app {
  font-family: "Roboto Mono", monospace;
  text-align: center;
  margin-top: 60px;
}
</style>

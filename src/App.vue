<template>
  <div class="container">
    <h2 class="title">Stocks</h2>
    <Stocks />
  </div>
</template>

<script>
import Stocks from "./components/Stocks.vue";

export default {
  name: "App",
  components: {
    Stocks,
  },
};
</script>

<style>
.title {
  text-align: center;
}
</style>
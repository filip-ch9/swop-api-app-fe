<template>
  <div id="app">
    <ExchangeRates />
  </div>
</template>

<script>
import ExchangeRates from './components/ExchangeRates.vue';

export default {
  name: 'App',
  components: {
    ExchangeRates
  }
}
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
</style>

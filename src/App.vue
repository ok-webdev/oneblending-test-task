<template>
  <div id="app">
    <crashes-list />
  </div>
</template>

<script>
import CrashesList from './components/CrashesList';

export default {
  components: {
    CrashesList: CrashesList
  }
}
</script>

<style>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>

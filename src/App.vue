<template>
  <img alt="Vue logo" src="./assets/logo_bw.png">
  <Conversion/>
</template>

<script>
import Conversion from './components/Conversion.vue'

export default {
  name: 'App',
  components: {
    Conversion
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

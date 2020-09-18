<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <meteo></meteo>
  </div>
</template>

<script>
import Meteo from './components/Meteo.vue'

export default {
  name: 'App',
    components: {
        'meteo': Meteo
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
body {
  background: #43C6AC;
  background: linear-gradient(to right, #f8ffae, #43c6ac) ;
}
</style>

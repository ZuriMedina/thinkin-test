<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Compatibilidad msg="Compatibilidad de Elementos"/>
  </div>
</template>

<script>
import Compatibilidad from './components/Compatibilidad.vue'

import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name: 'app',
  components: {
    Compatibilidad
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

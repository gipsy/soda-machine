<template>
  <SodaView/>
</template>

<script>
import SodaView from './views/SodaView'

export default {
  name: 'App',
  components: {
    SodaView
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Amatic+SC:wght@700&family=Lobster&family=Pacifico&display=swap');
html, body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Amatic SC', cursive;
  font-family: 'Lobster', cursive;
  font-family: 'Pacifico', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  background-color: darkslategrey;
  height: 100vh;
  padding-top: 20px;
}
</style>

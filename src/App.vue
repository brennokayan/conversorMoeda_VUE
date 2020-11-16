<template>
  <div>
    <Conversor moeda-a = "USD" moeda-b = "BRL"/>
  </div>
 
</template>

<script>
import Conversor from './components/Converso'
export default {
  name: 'App',
  components: {
    Conversor
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

<template>
  <div id="app">
   
    <Event></Event>
    
   </div>
</template>

<script>

 //import DelivaryNote from './components/DelivaryNote';
// import Test from './components/Test';
 import Event from './components/Eevnt';
  
window.axios = require('axios');
window.axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest'
 

export default {
  name: 'app',
  
  components: {
  //   Test , DelivaryNote , 
  Event
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

<template>
  <div class="container-fluid mt-3">
    <div class="jumbotron">
      <h1>Proyecto Tp4</h1>
      <hr>

      <Navbar />
      <router-view></router-view>
      

    </div>
  </div>
</template>

<script>

import Navbar from './componentes/Navbar.vue'


export default {
  name: 'App',
  components: {
  
    Navbar,
    
  }
}
</script>

<style>


</style>

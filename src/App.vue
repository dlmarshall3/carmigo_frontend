<template>
  <div id="app" class="container-fluid">
    <vinHeader></vinHeader>
    <vinBody></vinBody>  
    <vinGarage></vinGarage>
  </div>
</template>

<script>
import vinHeader from './components/vinHeader.vue'
import vinBody from './components/vinBody.vue'
import vinGarage from './components/vinGarage.vue'

export default {
  name: 'App',
  components: {
    vinHeader,
    vinBody,
    vinGarage,
  }
}
</script>

<style>

html {
  min-height: 100%;
  background-image: url('assets/bg-3.png');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>

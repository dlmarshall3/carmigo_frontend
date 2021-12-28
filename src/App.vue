<template>
  <div id="app" class="container-fluid">
    <vinHeader></vinHeader>
    <vinBody></vinBody>
    <ContactUs></ContactUs>    
    <vinGarage></vinGarage>
  </div>
</template>

<script>
import vinHeader from './components/vinHeader.vue'
import vinBody from './components/vinBody.vue'
import vinGarage from './components/vinGarage.vue'
import ContactUs from './components/ContactUs.vue'

export default {
  name: 'App',
  components: {
    vinHeader,
    vinBody,
    vinGarage,
    ContactUs
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-image: url('assets/bg-md.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  color: #2c3e50;
  height: 100vh;
}
</style>

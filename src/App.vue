<template>
  <div id="app" class="container-fluid">
    <vinHeader></vinHeader>
    <vinBodyText></vinBodyText>
  </div>
</template>

<script>
import vinHeader from './components/vinHeader.vue'
import vinBodyText from './components/vinBodyText.vue'
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    vinHeader,
    vinBodyText
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
  background-image: url('assets/bg-md.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  height: 100vh;
}
</style>

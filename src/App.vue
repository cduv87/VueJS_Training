<template>
  <div id="app">
    <img src="./assets/logo_b.png">
    <HelloWorld msg="Hello World!"/>
    <p></p>
    <TestRed secretMsg="Bulbizard" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TestRed from './components/TestRed.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    TestRed
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

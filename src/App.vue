<template>
  <div id="app">
   
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style>
body{
  background-color: rgb(152, 152, 209);
}
</style>

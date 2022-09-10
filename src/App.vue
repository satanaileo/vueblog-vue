<template>
  <div id="app">
    <mavon-editor/>
    <router-view></router-view>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Header from "@/components/Header";
import mavonEditor from 'mavon-editor';

export default {
  name: 'app',
  components: {
    HelloWorld,
    Header,
    mavonEditor
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

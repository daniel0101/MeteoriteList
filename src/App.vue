<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <h1 class="text-3xl font-bold my-10">Meteorite Explorer</h1>
    <Search/>
    <List/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Search from './components/Search.vue';
import List from './components/MeteoriteList.vue';

export default {
  name: 'app',
  components: {
    Search,
    List
  },
  data: function(){
    return {
        query: ''
    }
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

<template>
  <div id="app">
    <img src="./assets/logo.png">
    <scroll/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Todos from './components/Todos'
import TableList from './components/TableList'
import Scroll from './components/Scroll'

export default {
  name: 'App',
  components: {
    HelloWorld, Todos, TableList, Scroll
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

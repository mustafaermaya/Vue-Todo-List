<template>
  <div id="app">
    <app-todos></app-todos>
  </div>
</template>

<script>
import Todos from './components/Todos'
export default {
  name: 'app',
  components: {
    appTodos : Todos
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
  margin-top: 0px;
}
</style>

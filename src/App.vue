<template>
  <div id="app">
    <h1>Notes</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;

  max-width: 600px;
  margin: 0 auto;
  line-height: 1.4;
  color: #32485F;
}

h1 {
  text-align: center;
}
</style>

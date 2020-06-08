<template>
  <div id="app">
    <todoList/>
  </div>
</template>

<script>
import todoList from './components/todoList.vue'

export default {
  name: 'App',
  components: {
    todoList
  }
}
</script>
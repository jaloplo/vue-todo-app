<template>
  <div id="app" class="section">
    <Todo />
  </div>
</template>

<script>
import Todo from './components/Todo.vue';

export default {
  name: 'app',
  components: {
    Todo
  }
}
</script>

<style>
@import url("https://cdnjs.cloudflare.com/ajax/libs/bulma/0.7.5/css/bulma.min.css");
</style>
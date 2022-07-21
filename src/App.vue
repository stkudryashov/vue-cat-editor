<template>
  <cat-editor />
</template>

<script>
import CatEditor from './components/CatEditor.vue'

export default {
  name: 'App',
  components: {
    CatEditor
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

  margin: 20px 60px;
}

h2 {
  margin-top: 0;
}
</style>

<template>
  <div id="app">
    <HeaderMenuBar/>
    <PostEditor/>
  </div>
</template>

<script>
import PostEditor from './components/PostEditor.vue'
import HeaderMenuBar from './components/HeaderMenuBar.vue'

export default {
  name: 'App',
  components: {
    PostEditor,
    HeaderMenuBar
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
}
</style>

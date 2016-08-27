<template>
  <div id="app">
    <Home></Home>
  </div>
</template>Topbar

<script>
import Topbar from './components/Topbar.vue'
import Home from './views/Home.vue'
export default {
  name: 'App',
  components: {
    Topbar,
    Home
  },
  data () {
    return {
      msg: 'Hello Vue!'
    }
  }
}
</script>

<style lang="sass">

  // Variables
  $lightgrey: #e8e8e8;

  body {
    background: $lightgrey;
    font-family: Helvetica, sans-serif;
  }
</style>

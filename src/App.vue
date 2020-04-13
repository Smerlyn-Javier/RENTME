<template>
  <div id="app">
   <navbar/>
  </div>
</template>

<script>
import Navbar from '../src/components/layouts/Navbar'

export default {
  name: 'App',
  components: {
    Navbar
  }
}
</script>

<style>
@import "../src/assets/global.scss";
@import "../src/assets/scss/mixins.scss";

</style>

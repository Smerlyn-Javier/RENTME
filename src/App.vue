<template>
  <div id="app">
   <navbar/>
   <carousel/>
  </div>
</template>

<script>
import Navbar from '../src/components/layouts/Navbar'
import Carousel from '../src/components/Carousel'

export default {
  name: 'App',
  components: {
    Navbar,
    Carousel
  }
}
</script>

<style>
@import "../src/assets/global.scss";
@import "../src/assets/scss/mixins.scss";

</style>

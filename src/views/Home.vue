<template>
  <div class="home">
    <img src="../assets/iphonex.png" class="iphonex">
    <img src="../assets/rappi_background.png" class="rappi_background">
    <Reviews/>
  </div>
</template>

<script>
// @ is an alias to /src
import Reviews from '@/components/Reviews.vue'

export default {
  name: 'home',
  components: {
    Reviews
  }
}
</script>

<style lang="sass">
  .iphonex
    left: calc(50vw - 160px)
    pointer-events: none
    position: absolute
    top: 8px
    width: 320px
    z-index: 20

  .rappi_background
    left: calc(50vw - 140px)
    position: absolute
    top: 24px
    width: 280px
    z-index: 1
</style>

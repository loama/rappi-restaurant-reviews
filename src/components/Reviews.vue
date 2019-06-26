<template>
  <div class="reviews">
    <div class="cards">
      <div class="card restaurant"></div>
      <div class="card dishes"></div>
      <div class="card thanks"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
  .reviews
    background: rgba(200, 200, 200, 0.90)
    height: 584px
    left: calc(50vw - 140px)
    overflow: hidden
    padding-top: 24px
    position: absolute
    top: 24px
    width: 280px
    z-index: 2

    .cards
      margin-top: 40px
      width: 500px

    .card
      background: #FFF
      border-radius: 8px
      box-shadow: 0 1px 3px #888
      display: inline-block
      height: 400px
      margin-left: 16px
      position: absolute
      width: 240px

      &.restaurant
        left: 0

      &.dishes
        left: 256px

      &.thanks
        left: 512px
</style>

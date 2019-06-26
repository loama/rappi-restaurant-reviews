<template>
  <div class="reviews">
    <div class="cards">
      <div class="card restaurant">
        <span class="title">¿Qué tal estuvo tu experiencia?</span>

        <div class="emojis">
          <div class="emoji"
               v-on:click="emoji_active = 1"
               v-bind:class="{active: emoji_active === 1}">
            <img src="../assets/emoji-1.png">
          </div>

          <div class="emoji"
               v-on:click="emoji_active = 2"
               v-bind:class="{active: emoji_active === 2}">
            <img src="../assets/emoji-2.png">
          </div>

          <div class="emoji"
               v-on:click="emoji_active = 3"
               v-bind:class="{active: emoji_active === 3}">
            <img src="../assets/emoji-3.png">
          </div>

          <div class="emoji"
               v-on:click="emoji_active = 4"
               v-bind:class="{active: emoji_active === 4}">
            <img src="../assets/emoji-4.png">
          </div>

          <div class="emoji"
               v-on:click="emoji_active = 5"
               v-bind:class="{active: emoji_active === 5}">
            <img src="../assets/emoji-5.png">
          </div>
        </div>
      </div>

      <div class="card dishes"></div>

      <div class="card thanks"></div>
    </div>

    <div class="restaurant-img">
      <img src="../assets/wlb.png">
    </div>

    <div class="previous-button"></div>
    <div class="next-button"></div>

    <div class="status-all"></div>
    <div class="status-current"></div>

  </div>
</template>

<script>
export default {
  data () {
    return {
      emoji_active: null
    }
  },
  name: 'reviews'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
  .reviews
    background: rgba(250, 250, 250, 0.92)
    height: 584px
    left: calc(50vw - 140px)
    overflow: hidden
    padding-top: 24px
    position: absolute
    top: 24px
    width: 280px
    z-index: 2

    .restaurant-img
      background: #F7EA5F
      border: 1px solid #909090
      border-radius: 50%
      height: 56px
      left: calc(112px)
      position: absolute
      top: 40px
      width: 56px

      img
        margin: 2px
        width: 48px

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
        height: 140px
        left: 0

        .emojis
          margin-top: 20px

          .emoji
            display: inline-block
            opacity: 0.3
            width: 48px

            &.active
              opacity: 1

            img
              width: 40px

      &.dishes
        left: 256px

      &.thanks
        left: 512px

    .title
      display: block
      font-family: 'CircularStd-Bold'
      font-size: 15px
      margin-top: 48px

    .next-button
      background: #F75D63
      border-radius: 8px
      bottom: 16px
      height: 48px
      left: 12px
      position: absolute
      width: 256px

    .status-all
      background: #DDD
      border-radius: 4px
      bottom: 72px
      height: 8px
      left: 12px
      position: absolute
      width: 256px

    .status-current
      background: #F75D63
      border-radius: 4px
      bottom: 72px
      height: 8px
      left: 12px
      position: absolute
      transition: all 0.3s
      width: 40px
</style>

<template>
  <div class="reviews" v-bind:class="current_step_in_letters">
    <div class="cards" v-bind:class="current_step_in_letters">
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

      <div class="card dishes">
        <div class="dish">
          <div class="dish-name">Hamburguesa Rockefeller</div>
          <div class="thumbs-down"
               v-bind:class="{active: dish_review_one === 'negative'}"
               v-on:click="dish_review_one = 'negative'">
            <img src="../assets/thumbs-down.png">
          </div>

          <div class="thumbs-up"
               v-bind:class="{active: dish_review_one === 'positive'}"
               v-on:click="dish_review_one = 'positive'">
            <img src="../assets/thumbs-up.png">
          </div>
        </div>

        <div class="dish">
          <div class="dish-name">Hamburguesa Gorgory</div>
          <div class="thumbs-down"
               v-bind:class="{active: dish_review_two === 'negative'}"
               v-on:click="dish_review_two = 'negative'">
            <img src="../assets/thumbs-down.png">
          </div>

          <div class="thumbs-up"
               v-bind:class="{active: dish_review_two === 'positive'}"
               v-on:click="dish_review_two = 'positive'">
            <img src="../assets/thumbs-up.png">
          </div>
        </div>

        <div class="dish">
          <div class="dish-name">Malteada de Vainilla</div>
          <div class="thumbs-down"
               v-bind:class="{active: dish_review_three === 'negative'}"
               v-on:click="dish_review_three = 'negative'">
            <img src="../assets/thumbs-down.png">
          </div>

          <div class="thumbs-up"
               v-bind:class="{active: dish_review_three === 'positive'}"
               v-on:click="dish_review_three = 'positive'">
            <img src="../assets/thumbs-up.png">
          </div>
        </div>
      </div>

      <div class="card thanks">
        <div class="thanks-title">¡Gracias!</div>
        <div class="thanks-details">Tus comentarios nos ayudan a mejorar</div>
      </div>
    </div>

    <div class="restaurant-img">
      <img src="../assets/wlb.png">
    </div>

    <div class="previous-button"
         v-on:click="current_step = current_step - 1"
         v-bind:class="current_step_in_letters">
      <img src="../assets/keyboard_backspace.svg">
    </div>

    <div class="next-button"
         v-on:click="current_step = current_step + 1"
         v-bind:class="[current_step_in_letters, next_active ? 'active' : '']"> {{next_text}} </div>

    <div class="status-all"></div>
    <div class="status-current"
         v-bind:class="current_step_in_letters"></div>

  </div>
</template>

<script>
export default {
  computed: {
    current_step_in_letters () {
      if (this.current_step === 0) {
        return 'zero'
      } else if (this.current_step === 1) {
        return 'one'
      } else if (this.current_step === 2) {
        return 'two'
      } else {
        return 'closed'
      }
    },
    dish_review_valid () {
      if (this.dish_review_one && this.dish_review_two && this.dish_review_three) {
        return true
      } else {
        return false
      }
    },
    next_active () {
      if (this.current_step === 0 && this.emoji_active !== null) {
        return true
      } else if (this.current_step === 1 && this.dish_review_valid) {
        return true
      } else if (this.current_step === 2) {
        return true
      } else {
        return false
      }
    },
    next_text () {
      if (this.current_step === 0) {
        return 'Siguiente'
      } else if (this.current_step === 1) {
        return 'Terminar'
      } else {
        return 'Cerrar'
      }
    }
  },
  data () {
    return {
      emoji_active: null,
      dish_review_one: null,
      dish_review_two: null,
      dish_review_three: null,
      current_step: 0
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
    opacity: 1
    overflow: hidden
    padding-top: 24px
    position: absolute
    transition: all 0.3s
    top: 24px
    width: 280px
    z-index: 2

    &.closed
      pointer-events: none
      opacity: 0

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
      transition: all 0.3s
      width: 500px

      &.zero
        transform: translate3d(0, 0, 0)

      &.one
        transform: translate3d(-248px, 0, 0)

      &.two
        transform: translate3d(-504px, 0, 0)

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
        color: #323232
        height: 200px
        left: 256px
        padding: 40px 8px 16px 8px
        text-align: left
        width: 224px

        .dish
          height: 40px
          margin-top: 24px
          vertical-align: center

          .dish-name
            display: inline-block
            vertical-align: top
            width: 128px

        .thumbs-up
          display: inline-block
          height: 44px
          opacity: 0.3
          width: 44px

          img
            margin: 8px
            width: 32px

          &.active
            opacity: 1

        .thumbs-down
          display: inline-block
          height: 44px
          opacity: 0.3
          width: 44px

          img
            margin: 8px
            width: 32px

          &.active
            opacity: 1

      &.thanks
        left: 512px
        padding-top: 40px
        height: 120px

        .thanks-title
          font-family: 'CircularStd-Bold'
          font-size: 28px

        .thanks-details
          color: #898989
          margin-top: 8px

    .title
      display: block
      font-family: 'CircularStd-Bold'
      font-size: 15px
      margin-top: 48px

    .previous-button
      border: 1px solid #D8D8D8
      border-radius: 8px
      bottom: 16px
      cursor: pointer
      height: 46px
      left: -36px
      position: absolute
      transform: translate3d(0, 0, 0)
      transition: all 0.3s
      width: 48px

      &.one
        transform: translate3d(48px, 0, 0)

      img
        margin: 10px 0
        opacity: 0.5

    .next-button
      background: #F75D63
      border-radius: 8px
      bottom: 16px
      color: #FFF
      cursor: pointer
      height: 48px
      left: 12px
      line-height: 48px
      opacity: 0.5
      pointer-events: none
      position: absolute
      transform: translate3d(0, 0, 0)
      transition: all 0.3s
      width: 256px

      &.active
        opacity: 1
        pointer-events: all

      &.one
        transform: translate3d(56px, 0, 0)
        width: 200px

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

      &.zero
        width: 85px

      &.one
        width: 170px

      &.two
        width: 256px
</style>

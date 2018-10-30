<template lang="pug">
  .main
    .card()
      .card__back(@click='flip' :style="{ 'background-image': 'url(' + cardback + ')' }")
      .card__front(:style="{ 'background-image': 'url(' + cardfront + ')' }")
</template>

<script>
export default {
  props: {
    cardfront: String,
    cardback: String
  },
  data () {
    return {}
  },
  methods: {
    flip (e) {
      this.$emit('pick', e.target)
    }
  }
}
</script>

<style lang="sass" scoped>
$cardwidth: 150px
$cardheight: 220px
.main
  height: $cardheight
  position: relative
  width: $cardwidth
  .card
    position: absolute
    width: 100%
    height: 100%
    transform-style: preserve-3d
    transition: .5s all ease
    &__back, &__front
      position: absolute
      backface-visibility: hidden
      background-size: contain
      background-repeat: no-repeat
      background-position: center
    &__back
      width: 100%
      height: 100%
    &__front
      width: 80%
      height: 80%
      top: 20%
      left: 20%
      margin-left: -($cardwidth/100*10)
      margin-top: -($cardheight/100*10)
      transform: rotateY(180deg)
.active, .reveal
  transform: rotateY(180deg)
</style>


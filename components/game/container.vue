<template lang="pug">
  .grid
    .flex(v-for='card in this.cards' md3)
      card(:cardfront='card' :cardback='back' @pick='pick')
</template>

<script>
import card from './card'
export default {
  created () {
    const cards = this.cards
    this.cards = cards.concat(cards).sort(() => Math.random() - 0.5)
  },
  components: {
    card
  },
  props: [
    'cards',
    'back'
  ],
  methods: {
    pick (e) {
      console.log(e, this.process)
      if (this.process) {
        return
      }
      const el = e
      console.log('jopa')
      el.parentNode.classList.add('active')
      this.tmp.push(el)
      console.log('tmp: ', this.tmp)
      if (this.tmp[1]) {
        const that = this
        console.log(!(that.tmp[1].style.backgroundImage.split('"')[1] === that.tmp[0].style.backgroundImage.split('"')[1]))
        this.process = true
        setTimeout(() => {
          if ((that.tmp[1].nextSibling.style.backgroundImage.split('"')[1] !== that.tmp[0].nextSibling.style.backgroundImage.split('"')[1])) {
            that.tmp.forEach(i => {
              i.parentNode.classList.remove('active')
            })
          }
          that.tmp.shift()
          that.tmp.shift()
          this.process = false
        }, 500)
      }
    }
  },
  data () {
    return {
      tmp: [],
      process: !1
    }
  }
}
</script>

<style lang="sass" scoped>
.grid
  margin: 0 auto
  display: grid
  grid-template-columns: repeat(4,150px)
  width: max-content
</style>

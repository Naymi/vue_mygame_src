<template lang="pug">
  v-container
    h2(style='text-align: center') Начнём!
    game-container(:cards='cards', :back='back')
</template>

<script>
import container from './container'
export default {
  components: {
    'game-container': container
  },
  data () {
    return {
      back: 'http://natpagle.ru/wp-content/uploads/2017/02/HCT-cardback.png',
      cards: [
        'https://upload.wikimedia.org/wikipedia/ru/thumb/3/39/Java_logo.svg/1200px-Java_logo.svg.png',
        'https://www.nixp.ru/uploads/news/fullsize_image/bc6e85e35944886749263e972b56e20a600a6a69.png',
        'https://avatars.mds.yandex.net/get-pdb/904462/23df2d90-5376-4409-aeda-1ec9ea23dcf7/s375',
        'http://itdistrict.ru/wp-content/uploads/2016/03/yazyik-programmirovaniya-JavaScript.png',
        'http://alllogos.ru/images/logotip-node-js.png',
        'https://www.nixp.ru/uploads/news/fullsize_image/3c154b61e5f47c4b7bb4fc37433d74422621e200.png'
      ]
    }
  }
}
</script>

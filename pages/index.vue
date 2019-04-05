<template>
  <main
    ref="content"
    class="h-screen background relative"
    :style="{backgroundImage: `url(${require('~/assets/img/background.jpg')})`}"
    @mousemove="calculatePosition"
  >
    <transition name="fade" mode="in-out">
      <img
        :key="chosenPicture"
        :src="pictures[pictures.length - chosenPicture - 1]"
        class="absolute wistiti-image object-cover"
      >
    </transition>
  </main>
</template>

<script>
export default {
  data() {
    return {
      position: 0,
      fullWidth: 0,
      chosenPicture: 0,
      pictures: [
        require('~/assets/img/tiff-0.png'),
        require('~/assets/img/tiff-1.png'),
        require('~/assets/img/tiff-2.png'),
        require('~/assets/img/tiff-3.png'),
        require('~/assets/img/tiff-4.png'),
        require('~/assets/img/tiff-5.png'),
        require('~/assets/img/tiff-6.png'),
        require('~/assets/img/tiff-7.png'),
        require('~/assets/img/tiff-8.png'),
        require('~/assets/img/tiff-9.png')
      ]
    }
  },

  mounted() {
    this.fullWidth = this.$refs.content.offsetWidth
  },

  methods: {
    calculatePosition(e) {
      this.chosenPicture = Math.round((e.clientX / this.fullWidth) * 9)
    }
  }
}
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity .1s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}

.wistiti-image {
  top: 240px;
  left: 260px;
  height: 375px;
}

.background {
  background-size: 1200px;
  background-repeat: no-repeat;
  background-color: #EAE6E3;
}
</style>

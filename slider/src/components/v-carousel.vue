<template>
  <div class="wrapper">
    <div class="v-carousel" :style="{'margin-left': '-' + (100 * currentSlideIndex) + '%'}">
      <v-carousel-item
          v-for="item in carousel_data"
          :key="item.id"
          :item_data="item"
      />
    </div>
    <button @click="prevSlide">Предыдущая</button>
    <button @click="nextSlide">Следующая</button>
  </div>
</template>

<script>
import vCarouselItem from './v-carousel-item.vue'

export default {
  name: "v-carousel",
  components: {
    vCarouselItem
  },
  props: {
    carousel_data: {
      type: Array,
      default: () => [],
    },
    interval: {
      type: Number,
      default: 0
    }
  },
  data () {
    return {
      currentSlideIndex: 0
    }
  },
  methods: {
    prevSlide() {
      if (this.currentSlideIndex <= 0) {
        this.currentSlideIndex = this.carousel_data.length - 1
      } else {
        this.currentSlideIndex --
      }
    },
    nextSlide() {
      if (this.currentSlideIndex >= this.carousel_data.length -1) {
        this.currentSlideIndex = 0
      } else {
        this.currentSlideIndex++
      }
    }
  },
  // mounted() {
  //   if (this.interval > 0) {
  //     let vm = this;
  //     setInterval(function () {
  //       vm.nextSlide()
  //     }, vm.interval)
  //   }
  // }
}
</script>

<style>
  .wrapper {
    max-width: 300px;
    overflow: hidden;
    margin: 0 auto;
  }
  .v-carousel {
    display: flex;
    transition: all ease .5s;
  }
</style>
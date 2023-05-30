<template>
  <div class="v-carousel-item">
    <img class="images"
        :src="imageSrc(item_data.img)"
        width="300"
        height="222"
        alt="image"
    v-if="imageSlide">
    <div class="item_content">
      <p>{{item_data.name}}</p>
      <p>{{item_data.id}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "v-carousel-item",
  props: {
    item_data: {
      type: Object,
      default: () => {}
    },
    imageSlide: {
      type: Boolean,
      default: true
    }

  },
  methods: {
    imageSrc(name) {
      return new URL(`../assets/images/${name}`, import.meta.url).href;
    },
  }
}
</script>

<style scoped>

</style>
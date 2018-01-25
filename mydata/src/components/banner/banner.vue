<template>
  <Carousel :autoplay="autoplay" v-model="value" :loop="loop" :autoplay-speed="autoplaySpeed">
    <CarouselItem v-for="(item, index) in imgSource" v-if="imgSource.length" :key="index">
      <div class="demo-carousel">
        <router-link :to="{path: item.path}" tag="div" class="cli">
          <img :src="item.src" />
        </router-link>
      </div>
    </CarouselItem>
</Carousel>
</template>

<script>
import {Carousel, CarouselItem} from 'iview'
export default {
  props: {
    imgSource: {
      type: Array,
      default: []
    },
    val: {
      type: Number,
      default: 0
    },
    autoplay: {
      type: Boolean,
      defualt: false
    },
    loop: {
      type: Boolean,
      defualt: false
    },
    autoplaySpeed: {
      type: Number,
      default: 2000
    }
  },
  data () {
    return {
      value: this.val
    }
  },
  components: {
    Carousel,
    CarouselItem
  }
}
</script>

<style scoped>
.demo-carousel{
  width: 100%;
}
.demo-carousel img{
  display: block;
  width: 100%;
}
.cli{
  cursor: pointer;
}
</style>

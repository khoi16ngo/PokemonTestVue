<template>
  <carousel :settings='settings'>
    <slide v-for="picture in pictures" :key="picture.id">
      <div class="carousel__item">
        <img :src="picture.filePath" />
      </div>
    </slide>
  </carousel>
</template>

<script lang='ts'>
import 'vue3-carousel/dist/carousel.css';
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel';

export default {
  name: 'PictureCarousel',
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
  data() {
    return {
      pictures: [],
      settings: {
        itemsToShow: 4,
        snapAlign: 'center',
        autoplay: "200",
        wrapAround: "true",
        transition: "2000"
      }
    }
  },
  created() {
    this.pictures = this.getPictures()
  },
  methods: {
    getPictures() {
      let pictures = []
      for(let i = 1; i < 11; i++){
        let picture = {
            id: i,
            filePath: '/src/assets/pokemons/pokemon'+i+'.jpg'
        }
        pictures.push(picture)
      }

      return pictures
    }
  },  
};
</script>

<style>
.carousel__item {
  height: 400px;
  width: 300px;
  background-color: black;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
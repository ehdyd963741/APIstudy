<template>
  <div class="movie" v-for="(item, index) in movieList" :key="index">
    <MovieList :propsdata = "item"/>
  </div>
</template>

<script>
import MovieList from '../components/MovieList.vue'
import { computed } from '@vue/runtime-core';
import {useStore} from 'vuex'

export default {
  components: {
    MovieList
  },

  setup () {
    const store = useStore();
    const movieList = computed( () => store.getters.getMovieList)
    return{
      movieList
    }
  }
}
</script>

<style scoped>
.movie{
  position: relative;
  display: block;
  width: 49%;
  background: #fff;
  margin-bottom: 70px;
  border-radius: 5px;
  color: #adaeb9;
  padding: 20px;
  box-shadow: 0px 13px 27px -5px rgba(50, 50, 93, 0.25),
            0 8px 16px -8px rgba(0, 0, 0, 0.3), 0 -6px 16px -6px rgba(0, 0, 0, 0.025);
  cursor: pointer;
}
@media screen and (max-width: 1000px) {
  .movie {
    width: 95%;
  }
}
</style>
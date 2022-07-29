<template>
  <div>
    <h1>Film:</h1>
    <div class="wrapper">
      <PosterItems v-for="film in films" :key="film.id"
        :imageUrl="film.poster_path"
        :title="film.title"
        :originalTitle="film.original_title"
        :originalLanguage="film.original_language"
        :vote="film.vote_average"
        :overview="film.overview"/>
    </div>
  </div>
</template>

<script>
import PosterItems from './PosterItems.vue';
export default {
    props: ["films"],
    components: { PosterItems }
}
</script> 

<style lang="scss" scoped>
@import'../styles/generals.scss';

  .wrapper{
    display: flex;
    flex-wrap: wrap;
    }
    
  h1{
    color: $black;
    text-align: center;
    font-size: 60px;
    margin-bottom: 20px;
  }
</style>
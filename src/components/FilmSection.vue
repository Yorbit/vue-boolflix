<template>
  <div>
    <h1>Film:</h1>
    <div>
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
<template>
  <div>
    <h1>Serie:</h1>
    <div class="wrapper-down">
      <PosterItems v-for="tvSeries in tvSeries" :key="tvSeries.id"
        :imageUrl="tvSeries.poster_path"
        :title="tvSeries.name"
        :originalTitle="tvSeries.original_name"
        :originalLanguage="tvSeries.original_language"
        :vote="tvSeries.vote_average"
        :overview="tvSeries.overview"/>
    </div>
  </div>
</template>

<script>
import PosterItems from './PosterItems.vue';
export default {
    props: ["tvSeries"],
    components: { PosterItems }
}
</script>

<style lang="scss" scoped>
@import'../styles/generals.scss';

  .wrapper-down{
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
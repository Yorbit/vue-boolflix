<template>
  <div id="app">
    <BaseHeader @search="textToSearch"/>
    <BaseMain
      :tvSeries="searchedTvSeries"
      :films="searchedFilm"/>
  </div>
</template>


<script>
import BaseHeader from './components/BaseHeader.vue';
import BaseMain from './components/BaseMain.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    BaseHeader,
    BaseMain
  },

  data: function(){
    return{
      searchedTvSeries: [],
      searchedFilm: [],
      apiKey: '632d88dbb161f7c4a52120c619baaeb9',
    }
  },

  methods: {
    textToSearch(inputSearch){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&language=it-IT&query=${inputSearch}`)
      .then((result) => {
        console.log(inputSearch + 'film');
        this.searchedFilm = result.data.results;
        console.log(this.searchedFilm);
      })
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&language=it-IT&query=${inputSearch}`)
      .then((resultSeries) => {
        console.log(inputSearch + 'serie');
        this.searchedTvSeries = resultSeries.data.results;
        console.log(this.searchedTvSeries);
      })
    },
  }
}

</script>

<style lang="scss">
@import'./styles/generals.scss';
@import'../node_modules/flag-icons/css/flag-icons.css';
</style>
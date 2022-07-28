<template>
  <div id="app">
    <BaseHeader @search="textToSearch"/>
    <BaseMain
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
      searchedFilm: [],
      apiKey: '632d88dbb161f7c4a52120c619baaeb9',
    }
  },

  methods: {
    textToSearch(inputSearch){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${inputSearch}`)
      .then((result) => {
        console.log(inputSearch + 'film');
        this.searchedFilm = result.data.results;
        console.log(this.searchedFilm);
      })
    },
  }
}

</script>

<style lang="scss">
@import'./styles/generals.scss';
</style>
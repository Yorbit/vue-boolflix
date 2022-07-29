<template>
  <div>
    <div v-if="isArrayEmpty()">
      <h1 class="Film-Non-Trovato">ELEMENTO NON TROVATO</h1>
    </div>
    <div v-else>
      <div class="films-container">
        <FilmSection 
            :films="films"/>
      </div>
      <div class="series-container">
        <SeriesSection 
            :tvSeries="tvSeries"/>
      </div>
    </div>
  </div>
</template>

<script>
import FilmSection from "./FilmSection.vue";
import SeriesSection from "./SeriesSection.vue";
export default {
    props: ['films', 'tvSeries'],
    
    components: { FilmSection, SeriesSection },
  data: function(){
    return{
      isEmpty: true,
    }
  },
  methods: {
    isArrayEmpty(){
      if ((this.films.length == 0) && (this.tvSeries.length == 0)) {
        return this.isEmpty = true;
      } else {
        return this.isEmpty = false;
      }
    }
  }
}
</script>
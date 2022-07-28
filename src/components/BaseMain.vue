<template>
  <div>
    <div v-if="isArrayEmpty()">
      <h1 class="Film Non Trovato">NON TROVATO</h1>
    </div>
    <div v-else>
      <div class="films-container">
        <FilmSection 
            :films="films"
        />
      </div>
    </div>
  </div>
</template>


<script>
import FilmSection from "./FilmSection.vue";
export default {
    props: ['films'],
    
    components: { FilmSection },
  data: function(){
    return{
      isEmpty: true,
    }
  },
  methods: {
    isArrayEmpty(){
      if (this.films.length == 0) {
        return this.isEmpty = true;
      } else {
        return this.isEmpty = false;
      }
    }
  }
}
</script>
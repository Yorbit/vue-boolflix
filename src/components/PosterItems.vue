<template>
  <div class="poster-parent">
    <ul class="poster"         
        :style="{'background-image': `url(${baseUrlDimension}${imageUrl})`}">
        <div v-if="hover">
          <h4> <strong>Titolo:</strong>  
            {{ title }}
          </h4>
          <h4> <strong>Titolo originale:</strong>  
            {{ originalTitle }}
          </h4>
          <span :class="`fi-${returnStringFlag(originalLanguage)} fi flag`"></span>
          <span> <strong>Voto:</strong> 
            <i class="fa-solid fa-star" v-for="(star, index) in changeVoteIntoStars(vote)" :key="index"></i>
          </span>
          <p>{{ overview }}</p>
        </div>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    imageUrl: String,
    title: String,
    originalTitle: String,
    originalLanguage: String,
    vote: Number,
    overview: String,
  },

  data: function(){
    return{
      baseUrlDimension: 'https://image.tmdb.org/t/p/w342/',
      hover: false,
    }
  },

    methods: {
    returnStringFlag(originalLanguage){
      const language = String(originalLanguage);

      switch (language) {
        case 'it':
          return 'it';

        case 'en':
          return 'gb';

        case 'ja':
          return 'jp';

        case 'de':
          return 'de';

        case 'es':
          return 'es';
        default:
          return 'not-present';
      }
    },
  },
}
</script>

<style lang="scss" scoped>
@import'../styles/generals.scss';

  .poster-parent{
    width: calc(90% / 5);
    height: 500px;
    margin: 0px 15px 25px 20px;

    }
    .poster{
      cursor: pointer;
      border: 1px solid black;
      height: 100%;
      list-style: none;
    }  
</style>
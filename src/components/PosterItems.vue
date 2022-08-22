<template>
  <div class="poster-parent">
    <ul class="poster" 
        @mouseover="hover = true"
        @mouseleave="hover = false"        
        :style="{'background-image': `url(${baseUrlDimension}${imageUrl})`}">
      <transition name="shadow">
        <div class="hover-item" v-if="hover">
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
      </transition>
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
    changeVoteIntoStars(vote){
      let newVote = Math.ceil((vote * 5) / 10);
      return newVote;
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

    .hover-item{
      height: 100%;
      padding: 20px;
      overflow: auto;
      background-color: gray;
      color: white;
      text-align: start;
      p{
        margin: 20px 0px;
        text-align: center;
      }
      h4, span{
        margin-bottom: 20px;
      }
     }
    .poster{
      cursor: pointer;
      border: 1px solid black;
      height: 100%;
      list-style: none;
      } 
    .flag{
        display: block;
        width: 20px;
        height: 20px;
      }
    span>i{
        color: gold;
      }
      .shadow-enter, .shadow-leave-to{
        opacity: 0;
      }
      .shadow-enter-active, .shadow-leave-active {
        transition: opacity .5s;
      } 
    }
</style>
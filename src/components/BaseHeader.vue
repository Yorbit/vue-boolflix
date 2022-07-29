<template>
  <div class="container">
    <div>
        <h1>BOOLFIX</h1>
    </div>
    <div>
        <input @keyup.enter="$emit('search', inputSearch)" type="text" placeholder="Cerca Un Film"
            v-model="inputSearch">

        <button @click="$emit('search', inputSearch)">CERCA</button>
    </div>
  </div>
</template>


<script>
export default {
    data: function(){
        return{
            inputSearch: '',
        }
    },
}
</script>

<style lang="scss" scoped>
@import'../styles/generals.scss';

    .container{
        background-color: $black;
        justify-content: space-around;
        padding: 20px;
        display: flex;
        align-items: center;


        input{
            margin-right: 10px;
            padding: 10px;
        }

        button{
            cursor: pointer;
            font-weight: bold;
            background-color: $black;
            border-color: $red;
            padding: 10px;
            color: white;
        }

        h1{
            color: $red;
            cursor: pointer;
        }
    }
</style>

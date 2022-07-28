<template>
  <div class="container">
    <div>
        <h1>BOOLFIX</h1>
    </div>
    <div>
        <input @keyup.enter="$emit('search', inputSearch)" type="text" placeholder="Cerca Un Film"
            v-model="inputSearch">

        <button @click="$emit('search', inputSearch)">
            Cerca
        </button>
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

<template>
<!-- creo div container della searchbar -->
  <div class="ms_search_section">
      <div class="ms_boolflix_logo">BOOLFLIX</div>
      <div>
        <input v-model="filmName" type="text" name="" id="" class="ms_text_area" placeholder="Cerca il titolo di un film">
        <button @click="$emit('passedFilm', filmName)"  class="ms_search_button">Cerca</button>
      </div>
     
  </div>
</template>

<script>
//Dati dell'export
export default {
    name: 'SearchBar',

    //Sezione con i Data()
    data(){
        return{
        filmName: '',
        }
    }
}

//sezione con i methods

</script>

<style lang="scss" scoped>
//importo stile della search bar
@import '../assets/SearchBar.scss';
</style>
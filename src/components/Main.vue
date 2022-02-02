<template>
  <div @passedFilm="getFilmCards" class="container">
      
  </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Main',
    //data
    data(){
        return{
            apiUrl: 'https://api.themoviedb.org/3/search/movie',
            filmsArray: [],

        }
    },
    //metodi
    methods:{
        getFilmCards: function(){
            axios
            .get(this.apiUrl, {
            params : {
                api_key: fbb85452ee66bae138619692ec4e952d,
                language: en-US,
                query: Spiderman,

                }//chiusura axios.get params
            }//chiusura oggetto interno axios.get
            
            )//chiusura axios.get
            .then( (response) => {
                this.filmsArray = response.data.results
                console.log(response.data.results)   //SONO FERMO QUI E NON SO COSA SUCCEDE Né FACENDO COSì Né DOPO
            })
        }
    }//chiusura methods
}//chiusura export
</script>

<style>

</style>
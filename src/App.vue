<template>
  <div id="app">
    <SearchBar @passedFilm="generateCards" />
    <!-- <div v-if="productsArray.length == 0">
      hey
    </div> -->
    <Main :filmsArray="filmsArray" :tvShowArray="tvShowArray" />
    
    
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import Main from './components/Main.vue'
import axios from 'axios'
export default {
  
  name: 'App',
  components: {
    SearchBar,
    Main
  },
  data(){
        return{
            apiUrlFilms: 'https://api.themoviedb.org/3/search/movie',
            apiUrlTvShow: 'https://api.themoviedb.org/3/search/tv',
            apiKey: 'fbb85452ee66bae138619692ec4e952d',
            filmsArray:[],
            tvShowArray:[],
           
            
        }
    },
    //metodi
    methods:{
        getFilmCards: function(filmName){
            axios
            .get(this.apiUrlFilms, {
            params : {
                api_key: this.apiKey,
                query: filmName,

                }//chiusura axios.get params
            }//chiusura oggetto interno axios.get
            
            )//chiusura axios.get
            .then( (response) => {
                this.filmsArray = response.data.results
                   //SONO FERMO QUI E NON SO COSA SUCCEDE Né FACENDO COSì Né DOPO
            })
        },
        getTvShow: function(filmName){
            axios
            .get(this.apiUrlTvShow, {
            params : {
                api_key: this.apiKey,
                query: filmName,

                }//chiusura axios.get params
            }//chiusura oggetto interno axios.get
            
            )//chiusura axios.get
            .then( (response) => {
                this.tvShowArray = response.data.results
                console.log(this.tvShowArray)   //SONO FERMO QUI E NON SO COSA SUCCEDE Né FACENDO COSì Né DOPO
            })
            .catch(error  => {
              console.log(error)
            })
            .finally(function() {
              console.log('prova')
            })
        },
        generateCards(filmName){
          this.getFilmCards(filmName),
          this.getTvShow(filmName)
        }
          
    }//chiusura methods
}
</script>

<style lang="scss">
@import url('./assets/Global.scss');
</style>

<template>
  <div id="app">
    <SearchBar @passedFilm="getFilmCards" />
    <Main :sonPropsArray="filmsArray"/>
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
            filmsArray: [],
        }
    },
    //metodi
    methods:{
        getFilmCards: function(filmName){
            axios
            .get(this.apiUrlFilms, {
            params : {
                api_key: 'fbb85452ee66bae138619692ec4e952d',
                query: filmName,

                }//chiusura axios.get params
            }//chiusura oggetto interno axios.get
            
            )//chiusura axios.get
            .then( (response) => {
                this.filmsArray = response.data.results
                console.log(response.data.results)   //SONO FERMO QUI E NON SO COSA SUCCEDE Né FACENDO COSì Né DOPO
            })
        }
    }//chiusura methods
}
</script>

<style lang="scss">
@import url('./assets/Global.scss');
</style>

<template>
  <div>
      <div v-if="filmsArray.length == 0 && tvShowArray.length == 0" class="ms_loading">
            <div class="ms_loading_content">
                <p>Benvenuto su </p>
                <p><span>BoolFlix</span></p> 
                <p>cerca un film o una serie TV per iniziare</p>
            </div>  
      </div>
      <div class="container" v-else>
      <ul v-for="(film, index) in filmsArray" :key="index" class="ms_filmCard">
            <li><img :src="`https://image.tmdb.org/t/p/w342/` + film.poster_path" alt="" class="ms_film_poster"></li>
            <li class="ms_film_name">{{film.title}}</li>
            <li>{{film.original_title}}</li>
            <li><img :src="getLangFlag(film.original_language)" class="ms_film_lang_img" alt=""> </li>
            <li>Voto degli utenti: {{film.vote_average}}</li> 
      </ul>
      <ul v-for="(film, index) in tvShowArray" :key="index+'serie'" class="ms_filmCard serie">
            <li><img :src="`https://image.tmdb.org/t/p/w342/` + film.poster_path" alt="" class="ms_film_poster"></li>
            <li class="ms_film_name">{{film.title}}</li>
            <li>{{film.original_title}}</li>
            <li><img :src="getLangFlag(film.original_language)" class="ms_film_lang_img" alt=""> </li>
            <li>Voto degli utenti: {{film.vote_average}}</li>
      </ul>
  </div>
  </div>
</template>

<script>
export default {
    name: 'Main',
    //data
    props: {
        filmsArray: Array,
        tvShowArray: Array,
    },
    methods:{
        getLangFlag: function(filmLang){
            let urlFlag = 'https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Gay_Pride_Flag.svg/2560px-Gay_Pride_Flag.svg.png';
            if(filmLang == 'en'){
                urlFlag = 'https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Flag_of_the_United_Kingdom_%283-2_aspect_ratio%29.svg/1280px-Flag_of_the_United_Kingdom_%283-2_aspect_ratio%29.svg.png';
            }else if(filmLang == 'it'){
                urlFlag = 'https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1280px-Flag_of_Italy.svg.png'
            }
            return urlFlag
        },//chiusura funzione getFilmLang
    }//chiusura methods
}//chiusura export
</script>

<style lang="scss" scoped>
@import '../assets/Vars.scss';
@import '../assets/main.scss';

</style>
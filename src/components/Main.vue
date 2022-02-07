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
        <h1>Film</h1>
        <div class="filmSection">
            <ul v-for="(film, index) in filmsArray" :key="index" class="ms_filmCard">
            <li>
                <img :src="`https://image.tmdb.org/t/p/w342/` + film.poster_path" alt="" class="ms_film_poster">
            </li>
            <div class="cardInfos">
                <li class="ms_film_name">{{film.title}}</li>
                <li>{{film.original_title}}</li>
                <li><img :src="getLangFlag(film.original_language)" class="ms_film_lang_img" alt=""> </li> 
                <li>
                    <span v-for="(elem, index) in getStar(film.vote_average)" :key="index"><i class="fas fa-star ms_vote_stars"></i></span>
                    <span v-for="(elem, index) in (5-getStar(film.vote_average))" :key="index+'films'"><i class="far fa-star ms_vote_stars"></i></span>
                </li>
                <li>{{film.overview}}</li>
            </div>
      </ul>
        </div>
    <h1>TV Show</h1>
      <div class="tvShowSection">
          <ul v-for="(film, index) in tvShowArray" :key="index+'serie'" class="ms_filmCard serie">
            <li>
                <img :src="`https://image.tmdb.org/t/p/w342/` + film.poster_path" alt="" class="ms_film_poster">
            </li>
            <div class="cardInfos">
                <li class="ms_film_name">{{film.name}}</li>
                <li>{{film.original_name}}</li>
                <li><img :src="getLangFlag(film.original_language)" class="ms_film_lang_img" alt=""> </li>
                <li>
                    <span v-for="(elem, index) in getStar(film.vote_average)" :key="index"><i class="fas fa-star ms_vote_stars"></i></span>
                    <span v-for="(elem, index) in (5-getStar(film.vote_average))" :key="index+'films'"><i class="far fa-star ms_vote_stars"></i></span>
                </li>
                <li>{{film.overview}}</li>
            </div>
      </ul>
      </div>
      
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
        getStar: function(voto){
            return Math.ceil(voto/2);
        },
    }//chiusura methods
}//chiusura export
</script>

<style lang="scss" scoped>
@import '../assets/Vars.scss';
@import '../assets/main.scss';
</style>
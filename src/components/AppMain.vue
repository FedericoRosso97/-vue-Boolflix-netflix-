<script >
import axios from 'axios';
import searchBar from './searchBar.vue';
import cardFilm from './cardFilm.vue'
 export default {
    name: 'AppMain',
    data(){
      return {
        filmList:[],
          apiLink:'https://api.themoviedb.org/3/search/movie?api_key=05e361d095d6a9d0db65612c54a8d5f5&query=back&include_adult=false&language=en-US&page=1'
      }
    },
    components: {
       searchBar,
       cardFilm,
    },
    methods:{
        getMovies(search){
        axios.get(this.apiLink,{
            params:{
            query:search,
          }
        })
      .then( (response) => {
    // handle success
        console.log(response);
        console.log(response.data.results)
        this.filmList=response.data.results
        console.log(this.filmList)
        })
        .catch(function (error) {
    // handle error
        console.log(error);
         })
       
    },

    },
    create(){
        this.getMovies
    }

   
}
</script>

<template>
    <header>
        <searchBar @searched="getMovies" />
        
    </header>
  <main>
    <div class="container">
        
     <div class="row">
        <div class="col-3 d-felx p-2 myCard">
            <cardFilm v-for="films in filmList"
            :filmElement="films"
            />
            
         <!-- <p>Titolo:{{ filmList[index].title }}</p>
          <p>Titolo originale:{{ filmList[index].original_title }}</p>
          <p>Lingua originale:{{ filmList[index].original_language}}</p>
          <p>Voto:{{ filmList[index].vote_average }}</p>-->
        </div>
     </div>
    </div>
    
  </main>
</template>

<style scoped>
  .myCard{
    border:1px solid black;
  }
</style>
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
        console.log(response);
        console.log(response.data.results)
        this.filmList=response.data.results
        console.log(this.filmList)
        })
        .catch(function (error) {
         console.log(error);
         })
    },
     
     //fine methods
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
        <div class="row wrap-nowrap">
            <cardFilm v-for="films in filmList"
            :filmElement="films"
            />
        </div>
    </div>
            
  </main>
</template>

<style scoped>
 
</style>
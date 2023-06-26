<script >
import axios from 'axios';
import searchBar from './searchBar.vue';
import cardFilm from './cardFilm.vue';
import cardSeries from './cardSeries.vue';
 export default {
    name: 'AppMain',
    data(){
      return {
        isVisible:false,
        filmList:[],
        seriesList:[],
        apiFilmsLink:'https://api.themoviedb.org/3/search/movie?api_key=05e361d095d6a9d0db65612c54a8d5f5&query=back&include_adult=false&language=en-US&page=1',
        apiSeriesLink:'https://api.themoviedb.org/3/search/tv?api_key=05e361d095d6a9d0db65612c54a8d5f5&language=it_IT&query=back'
      }
    },
    
    components: {
       searchBar,
       cardFilm,
       cardSeries,
    },
    
    methods:{
      getMovies(search){
        axios.get(this.apiFilmsLink,{
            params:{
            query:search,
          }
        })
       .then( (response) => {
        this.filmList=response.data.results
        console.log(this.filmList)
        })
        .catch(function (error) {
         console.log(error);
         })
      },
   
      getSeries(search){
        axios.get(this.apiSeriesLink,{
            params:{
            query:search,
          }
        })
       .then( (response) => {
        this.seriesListList=response.data.results
        console.log(this.filmList)
        })
        .catch(function (error) {
         console.log(error);
         })
      },
      
      searchApi(search){
        this.getMovies(search)
        this.getSeries(search)
        this.isVisible=true
      }
     
     //fine methods
    },
    
    create(){
        this.getMovies
    }
}
</script>

<template>
    <header>
        <searchBar @searched="searchApi" />
    </header>
  <main>
    <div class="container">
        <div class="row wrap-nowrap">
            <cardFilm v-for="films in filmList"
             :filmElement="films"
            />
            <h1 v-if="isVisible">Serie Tv</h1>
            <cardSeries v-for="series in filmList"
             :seriesElement="series"
            />
        </div>
    </div>
            
  </main>
</template>

<style scoped>
 
</style>
<script >
import axios from 'axios';
 export default {
    name: 'AppMain',
    data(){
      return {
        filmList:[],
          apiLink:'https://api.themoviedb.org/3/search/movie?api_key=05e361d095d6a9d0db65612c54a8d5f5&query=back&include_adult=false&language=en-US&page=1'
      }
    },
    components: {

    },
    created(){
        axios.get(this.apiLink)
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
  .finally(function () {
    // always executed
  })
  
    }

}
</script>

<template>
  <div>
    <h1>Main.Qui andranno tutti i films</h1>
    <div v-for="(films,index) in filmList">
      {{ filmList[index].original_title }}
    </div>
  </div>
</template>

<style scoped>

</style>
<script >
import axios from 'axios';
 export default {
    name: 'AppMain',
    data(){
      return {
          apiLink:'https://api.themoviedb.org/3/search/movie?query=05e361d095d6a9d0db65612c54a8d5f5&include_adult=false&language=en-US&page=1' 
      }
    },
    components: {

    },
    created(){
        axios.get(this.apiLink)
  .then(function (response) {
    // handle success
    console.log(response);
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
  </div>
</template>

<style scoped>

</style>
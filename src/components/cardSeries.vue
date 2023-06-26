<script >
    export default {
    name: 'cardFilm',
    props:{
       seriesElement: Object
    },
    data(){
      return {
         flags:['en.jpg','fr.jpg','it.png',],
      }
    },
    methods:{
      isFlagPresent(language){
         if(this.flags.includes(language+'.jpg')){
          return true
         }
         return false;
     },

     getImagePath(imgSource){
      return new URL(`../assets/img/${imgSource}.jpg`, import.meta.url);
     }
    }
    
}
   </script>
   
   <template>
         <div class="col-3 p-2 myCard "> 
            <p>Titolo:{{ seriesElement.title }}</p>
            <p>Titolo originale:{{ seriesElement.original_title }}</p>
            <div>
               <span v-if="isFlagPresent(seriesElement.original_language)">
                  <span>Lingua originale:</span><img  
                  :src="getImagePath(seriesElement.original_language)" alt="img">
               </span>
              
               <span v-else>
                  <p>Lingua originale:{{ seriesElement.original_language}}</p>
               </span>
            </div>
            <p>Voto:{{ seriesElement.vote_average }}</p>
         </div>
   </template>
   
   <style scoped>
    .myCard{
    border:1px solid black;
    
  }
  img{
   width: 5vw;
  }

   </style>
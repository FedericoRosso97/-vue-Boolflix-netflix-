<script >
    export default {
    name: 'cardFilm',
    props:{
       filmElement: Object
    },
    data(){
      return {
         flags:['en.jpg','fr.jpg','it.png',],
      }
    },
    methods:{
      isFlagPresent(language){
         if(this.flags.includes(language+'.jpg')){
            console.log('true')
          return true
         }
         console.log('false')
         return false;
     },

     getImagePath(imgSource){
      return new URL(`../assets/img${imgSource}.jpg`, import.meta.url);
     }
    }
    
}
   </script>
   
   <template>
         <div class="col-3 p-2 myCard "> 
            <p>Titolo:{{ filmElement.title }}</p>
            <div>
               <img v-if="isFlagPresent(filmElement.original_language)" 
               :src="getImagePath(filmElement.original_language)" alt="img">
               <span v-else>
                  <p>Lingua originale:{{ filmElement.original_language}}</p>
               </span>
            </div>
            <p>Titolo originale:{{ filmElement.original_title }}</p>
            <p>Voto:{{ filmElement.vote_average }}</p>
         </div>
   </template>
   
   <style scoped>
    .myCard{
    border:1px solid black;
  }
   </style>
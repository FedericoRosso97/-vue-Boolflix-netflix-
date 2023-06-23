<script >
    export default {
    name: 'cardFilm',
    props:{
       filmElement: Object
    },
    data(){
      return {
         
      }
    },
    methods:{
        
    }
    
}
   </script>
   
   <template>
        <div class="col-3 d-felx p-2 "> 
            <p>Titolo:{{ filmElement.title }}</p>
          <p>Titolo originale:{{ filmElement.original_title }}</p>
          <p>Lingua originale:{{ filmElement.original_language}}</p>
          <p>Voto:{{ filmElement.vote_average }}</p>
        </div>
   </template>
   
   <style scoped>
   
   </style>
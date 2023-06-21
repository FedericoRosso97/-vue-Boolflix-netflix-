<script >
    export default {
    name: 'SearchBar',
    data(){
      return {
          search:' ',
      }
    },
    
}
   </script>
   
   <template>
     <div class="d-flex">
        <input type="search" v-model="search">
        <button>Cerca</button>
        <p>{{search}}</p>
     </div>
   </template>
   
   <style scoped>
   
   </style>
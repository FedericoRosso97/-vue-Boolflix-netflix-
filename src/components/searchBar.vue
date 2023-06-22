<script >
    export default {
    name: 'SearchBar',
    proprs:{

    },
    data(){
      return {
          search:' ',
      }
    },
    methods:{
        
    }
    
}
   </script>
   
   <template>
     <div class="d-flex">
        <input type="search" v-model="search">
        <button @click="$emit('searched', search)">Cerca</button>
        <p>{{search}}</p>
     </div>
   </template>
   
   <style scoped>
   
   </style>
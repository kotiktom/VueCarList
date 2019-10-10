<template>
  <v-data-table
    :headers="headers"
    :items="cars"
    class="elevation-1"
  >
    <template v-slot:item.action="{item}">
    <v-btn  v-on:click="remove(item)">Delete</v-btn>
    </template>
  </v-data-table>
</template>


<script>
import axios from 'axios';
export default {
    
 name:'CarList',
 data() {
     
     return{
    headers: [
        {
        text: 'Brand',
            align: 'left',
            sortable: false,
            value: 'brand',
          },
          { text: 'Model', value: 'model' },
          { text: 'Year', value: 'year' },
          { text: 'Color', value: 'color' },
          { text: 'Price', value: 'price' },
          { text: 'Fuel', value: 'fuel' },
          { text: 'Actions', value:'action', sortable: false},
          
          
      
    ],   
         cars:[],
          } 
         },
         methods: {
        remove: function(car) {
        axios.delete(car._links.self.href)
        .then(res => {this.fetch()})        
      },

        fetch: function() {
        axios.get('https://carstockrest.herokuapp.com/cars')
        .then(response => (this.cars= response.data._embedded.cars))
        
      },

         },
    
         mounted() {
             axios.get('https://carstockrest.herokuapp.com/cars')
             .then(response=> (this.cars= response.data._embedded.cars))
             }
             } 
             </script> 




<style >
table {
    margin-left:auto; 
    margin-right:auto;
  }

</style>
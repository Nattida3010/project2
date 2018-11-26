<template>
    <div>
        <h1> Product List</h1>
        <!-- <ul>
            <li v-for="item in products" :key="item.id">
                {{item.id}} {{item.title}} {{item.price}}
            </li>
        </ul>
     -->
    
        <!-- <HelloWorld :msg="message"></HelloWorld> -->
          <b-table striped hover
           :items="products" 
           :fields="fields" 
            :per-page ="pageSize"
            :current-page="pageIndex"></b-table>
            
    <b-pagination  align="center"  size="md" :total-rows="products.length" v-model="pageIndex" :per-page="pageSize">
    </b-pagination>
    </div>
</template>
<script>
import axios from 'axios'
//import HelloWorld from '@/components/HelloWorld.vue'
export default {
    name : 'products',
    data(){
        return {
            message: 'Project 2',
            products:[],
            pageSize:10,
            pageIndex:1,
            fields:[
            {
                key:'id',
                sortable : true,
                  variant : 'info'
            },
            {
                key:'title',
                sortable : true,
               variant :'danger'
            },
            {
                key:'price',
                sortable : true,
                variant : 'success'
            },
            ],
        }
    },
    mounted(){
      var instance = this
        axios.get('https://shielded-spire-43023.herokuapp.com/api/products/')
        .then(function(response){
            console.log(response.data)
          instance .products = response.data.data
        })
    }
}
</script>

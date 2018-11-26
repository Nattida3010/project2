<template>
    <div>
        <h1> Product List</h1>
    
        <!-- <HelloWorld :msg="message"></HelloWorld> -->
    </div>
</template>
<script>
import axios from 'axios'
//import HelloWorld from '@/components/HelloWorld.vue'
export default {
    name : 'products',
    data(){
        return {
            message: 'Project 2'
        }
    },
    mounted(){
        axios.get('https://shielded-spire-43023.herokuapp.com/api/products/')
        .then(function(response){
            console.log(response.data)
        })
    }
}
</script>

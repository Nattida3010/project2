<template>
    <div>
        <h1>User</h1>
        <b-row>
      <b-col md="6" class="my-1">
        <b-form-group horizontal label="Filter" class="mb-0">
          <b-input-group>
            <b-form-input v-model="filter" placeholder="Type to Search" />
            <b-input-group-append>
              <b-btn :disabled="!filter" @click="filter = ''">Clear</b-btn>
            </b-input-group-append>
          </b-input-group>
        </b-form-group>
      </b-col>
      </b-row>
        <b-table striped hover 
          :items="users"
           :fields="fields" 
           :filter="filter"
            :per-page ="pageSize"
            :current-page="pageIndex"></b-table>
    </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'users',
  data(){
      return {
          message: 'Project2',
          users: [],
          
            pageSize:10,
            pageIndex:1,
            filter: null,
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
    computed: {
    sortOptions () {
      // Create an options list from our fields
      return this.fields
        .filter(f => f.sortable)
        .map(f => { return { text: f.label, value: f.key } })
    }
  },
  mounted () {
      var instance = this
      //this.users อ้างถึง instance
    axios
      .get('https://shrouded-plains-42723.herokuapp.com/api/purchase/')
      .then(function(response){
            console.log(response.data)
            instance.users = response.data.data
      })
}}
    

</script>
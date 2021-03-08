<template>
<div class="q-pa-lg home">
  <div class="row">
    <div class="col"><q-input v-model="ipaddress" label="IP address" /> </div>
    <div class="col"> <q-btn color="secondary" label="Get AWS IP address ranges" @click="findRange()" /> </div>
  </div>
  <br>
  <div class="row">
    <div class="col">
      <q-table
      title="Treats"
      :data="result"
      row-key="name"
      :pagination.sync="pagination"
    />
      
    </div>

  </div>

</div>
  
</template>

<script>

import axios from "axios"

export default {
  name: 'Home',
  components: {
    
  },
  data: function() {
    return {
      ipaddress: "3.10.127.32",
      result: [],
      pagination: {
        rowsPerPage: 30 // current rows per page being displayed
      },
    }
  },
  methods: {
    findRange(){
      var apiUrl = "https://23fhte6xu9.execute-api.us-east-1.amazonaws.com/alpha/ipfindv2?ip="

      apiUrl += this.ipaddress

      axios.get(apiUrl)
        .then(res=>{
          this.result = res.data.body
        })
      


    }
  }
}
</script>

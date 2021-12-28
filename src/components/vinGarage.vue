<template>

<div id="vinGarage">

   
    <h3 class="subtitle is-1">Your Garage</h3>

    <vinTable :vehicles="apiData"></vinTable>

    <form @submit.prevent>
    <label for="year"></label>
    <input v-model="year" name="year" type="number" placeholder="Year">
    <label for="make"></label>
    <input v-model="make" name="make" type="text" placeholder="Make">
    <label for="model"></label>
    <input v-model="model" name="model" type="text" placeholder="Model">
    <label for="color"></label>
    <input v-model="new_color" name="color" type="text" placeholder="Color">
     <button v-on:click="addVehicle">Submit</button>
    <button v-on:click="showVehicles">Display Garage</button>
    </form>
   
</div>

</template>

<script>

import vinTable from './vinTable.vue'

export default {
  name: 'vinGarage',
  components: {
      vinTable,
  },
  methods: {
    addVehicle(){
      const requestOptions = {
        method: 'POST',
        headers: { 'Content-Type': 'application/json'},
        body: JSON.stringify({
          year: this.year,
          make: this.make,
          model: this.model,
          new_color: this.new_color
        })
      }
      fetch('http://carmigo-master.herokuapp.com/api/v1/vehicles/', requestOptions)
    },
    showVehicles(){
      console.log('component mounted')
      const data = fetch('http://carmigo-master.herokuapp.com/api/v1/vehicles/')
      .then((response) => response.json())
      .then((responseData) => (this.apiData = responseData));
      this.apiData = data;
    }
  },
  data(){
    return {
      apiData: "",
      year: "",
      make: "",
      model: "",
      new_color: "",
    }
  },
}
</script>

<style>

#vinGarage {
    text-align: center;
    padding-top: 20px;
    padding-bottom: 20px;
    background-color: rgba(255,255,255,.6);
}
 

</style>
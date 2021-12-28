<template>

<div id="vinGarage" class="container-fluid">

   
    <h3 class="subtitle is-1">Your Garage</h3>
    <div class="columns">
    <div class="column" id="garageData">
      <vinTable :vehicles="apiData"></vinTable>
    </div>
    <div class="column">
      <form @submit.prevent id="vinForm">
      <label for="year"></label>
      <input v-model="year" name="year" type="number" placeholder="Year">
      <label for="make"></label>
      <input v-model="make" name="make" type="text" placeholder="Make">
      <label for="model"></label>
      <input v-model="model" name="model" type="text" placeholder="Model">
      <label for="color"></label>
      <input v-model="new_color" name="color" type="text" placeholder="Color">
      <button v-on:click="addVehicle">Submit</button>
      </form>
    </div>
    </div>
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
      .then(this.showVehicles())
      .then(this.showVehicles())
    },
    showVehicles(){
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
  mounted(){
    this.showVehicles()
  }
}
</script>

<style>

#vinGarage {
    text-align: center;
    padding-top: 20px;
    padding-bottom: 20px;
    background-color: rgba(255,255,255,.6);
}

#vinForm{
  display: flex;
  align-items: center;
  flex-direction: column;
}

#garageData{
  display: flex;
  align-items: center;
  flex-direction: column;
}
 

</style>
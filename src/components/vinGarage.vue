<template>

<div id="vinGarage" class="container-fluid">
  <h3 class="subtitle is-1">Your Garage</h3>
  <div class="columns is-two-thirds">
    <div class="column" id="garageData">
      <vinTable :vehicles="apiData"></vinTable>
    </div>
    <div class="column is-one-third">
      <form @submit.prevent id="vinForm" ref="formInput">

      <b-field>
        <b-input placeholder="Vehicle ID"
        type="number"
        icon-pack="fas"
        icon="id-card"
        v-model="id">
        </b-input>
      </b-field>

      <b-field>
        <b-input placeholder="Year"
        type="number"
        icon-pack="fas"
        icon="hashtag"
        v-model="year" required>
        </b-input>
      </b-field>

      <b-field>
        <b-input placeholder="Make"
        type="text"
        icon-pack="fas"
        icon="car"
        v-model="make" required>
        </b-input>
      </b-field>

      <b-field>
        <b-input placeholder="Model"
        type="text"
        icon-pack="fas"
        icon="truck-pickup"
        v-model="model" required>
        </b-input>
      </b-field>

      <b-field>
        <b-input placeholder="Color"
        type="text"
        icon-pack="fas"
        icon="palette"
        v-model="new_color" required>
        </b-input>
      </b-field>

      <div class="column" id="vinButtons">
      <b-button type="is-dark" v-on:click="addVehicle(); resetInputs()" class="vinButton">Submit</b-button>
      <b-button v-on:click="updateVehicle(id); resetInputs()" class="vinButton">Update Existing</b-button>
      </div>
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
          id: this.id,
          year: this.year,
          make: this.make,
          model: this.model,
          new_color: this.new_color
        })
      }
       fetch('http://carmigo-master.herokuapp.com/api/v1/vehicles/', requestOptions)
      let inputs = JSON.parse(requestOptions.body)
      if(Object.values(inputs).some(val => val === "")){
        alert('Missing fields')
      }
      else {
      fetch('http://carmigo-master.herokuapp.com/api/v1/vehicles/', requestOptions)
      .then(alert('Vehicle added'))
      .then(function setTimeout() { location.reload(), 200})
      }
      
 
    },
    showVehicles(){
      const data = fetch('http://carmigo-master.herokuapp.com/api/v1/vehicles/')
      .then((response) => response.json())
      .then((responseData) => (this.apiData = responseData));
      this.apiData = data;
    },
    updateVehicle(){
      
      const requestOptions = {
        method: 'PUT',
        headers: { 'Content-Type': 'application/json'},
        body: JSON.stringify({
          id: this.id,
          year: this.year,
          make: this.make,
          model: this.model,
          new_color: this.new_color
        })
      }
      let inputs = JSON.parse(requestOptions.body)
      if(Object.values(inputs).some(val => val === "")){
        alert('Missing field')
      }
      else {
      fetch(`http://carmigo-master.herokuapp.com/api/v1/vehicles/${this.id}`, requestOptions)
      .then(alert('Vehicle updated'))
      .then(function setTimeout() { location.reload(), 200})
      }
      
    },
    resetInputs(){
      this.$refs["formInput"].reset();
    }
  },
  data(){
    return {
      apiData: "",
      id: "",
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
  align-content: space-evenly;
}

#garageData{
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.vinButton {
  margin: 10px;
}
 

</style>
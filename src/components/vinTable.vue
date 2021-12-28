<template>
  <table id="vinTable">
      <thead>
          <tr>
              <th>Year</th>
              <th>Make</th>
              <th>Model</th>
              <th>Color</th>
          </tr>
      </thead>
      <tbody>
          <tr v-for="vehicle in vehicles" :key="vehicle.id">
              <td>{{ vehicle.year }} </td>
              <td>{{ vehicle.make }} </td>
              <td>{{ vehicle.model }} </td>
              <td>{{ vehicle.new_color }} </td>
              <td><i class="fas fa-trash" v-on:click="deleteVehicle(vehicle.id)"></i></td>
          </tr>
      </tbody>
  </table>
</template>

<script>



export default {
    name: 'vinTable',
    props: ['vehicles'],
    methods: {
        deleteVehicle(id){
        const requestOptions = {
        method: 'DELETE',
        headers: { 'Content-Type': 'application/json' },} 
      fetch(`http://carmigo-master.herokuapp.com/api/v1/vehicles/${id}`, requestOptions)
        .then(window.location.reload())
        },
    }
}

</script>

<style>

#tableDiv {
    text-align: center;
    display: flex;
    justify-content: center;
    align-content: space-evenly;
}

</style>
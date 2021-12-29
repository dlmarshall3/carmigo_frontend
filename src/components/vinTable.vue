<template>
    <div id="vinTable">

    <table id="vinTable">

        <thead>
            <tr><th v-show="isShow">ID</th>
                <th>Year</th>
                <th>Make</th>
                <th>Model</th>
                <th>Color</th>
            </tr>
        </thead>

        <tbody>
            <tr v-for="vehicle in vehicles" :key="vehicle.id">
                <td v-show="isShow">{{ vehicle.id }} </td>
                <td>{{ vehicle.year }} </td>
                <td>{{ vehicle.make }} </td>
                <td>{{ vehicle.model }} </td>
                <td>{{ vehicle.new_color }} </td>
                <td><i class="fas fa-trash" v-on:click="deleteVehicle(vehicle.id)"></i></td>
            </tr>
        </tbody>

    </table>
    </div>
</template>
    
    



<script>

export default {
    name: 'vinTable',
    props: ['vehicles', 'isShow'],
    // data: function() {
    //     return {
    //         isShow: true
    //     }
    // },

    //timeout is set to make sure user is notified the vehicle has been successfully deleted before page reload
    methods: {
        deleteVehicle(id){
        const requestOptions = {
        method: 'DELETE',
        headers: { 'Content-Type': 'application/json' },} 
      fetch(`//carmigo-master.herokuapp.com/api/v1/vehicles/${id}`, requestOptions)
      .then(alert('Vehicle deleted'))
      .then(function setTimeout() { location.reload(), 200})
        }
    }
}

</script>

<style>

#tableDiv {
    text-align: center;
    display: flex;
    justify-content: center;
    align-content: space-around;
}

#vinTable {
    width: 100%;
}

</style>
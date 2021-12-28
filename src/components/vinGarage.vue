<template>

<div id="vinGarage">
    <h3 class="subtitle is-1">Your Garage</h3>
    <form>
    <label for="year"></label>
    <input name="year" type="number" placeholder="Year">
    <label for="make"></label>
    <input name="make" type="text" placeholder="Make">
    <label for="model"></label>
    <input name="model" type="text" placeholder="Model">
    <label for="color"></label>
    <input name="color" type="text" placeholder="color">
    <button>Submit</button>
    </form>
</div>

</template>

<script>


export default {
  name: 'vinGarage',
  components: {
      
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
 

</style>
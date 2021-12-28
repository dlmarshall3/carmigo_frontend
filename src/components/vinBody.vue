<template>

<div id="vinBody" class="columns">
    <div class="column">
        <img src="./assets/sports.png">
    </div>
    <div class="column is-two-thirds">
      <p>Ever stay up late, wondering what high-end vehicle you plan on buying next? <i>(Yeah, same here.)</i> Well, look no further! VINsomnia is the easy way to keep track of the hot rod of your dreams when your burning wallet is keeping you from sleep. All you need to do is add the year, make, model, and color of the vehicle you're going to send your $12/hr assistant to purchase for you, and BOOM! The list is automatically updated. Change your mind? Finally pulled the trigger? You can delete that rig with the single click of a button!</p>
      <p>If you've enjoyed this page, please make sure to head over to my 
      <a href="https://github.com/dlmarshall3/carmigo_master">GitHub page</a> and give this repo a star.</p>
      <p>Once you're done driving that Maserati that costs more than your mortgage, that is.</p>
      <p><b>You rockstar, you.</b></p>
      <ContactUs/>
    </div>
</div>

</template>

<script>

import ContactUs from './ContactUs.vue'

export default {
  name: 'vinBody',
  components: {
      ContactUs
  }
}
</script>

<style>

#vinBody {
  padding-top: 30px;
  background-color: rgba(255,255,255,.6);
  padding-left: 20px;
  padding-right: 20px;
  line-height: 2.2;
  margin-bottom: 0px;
}

</style>

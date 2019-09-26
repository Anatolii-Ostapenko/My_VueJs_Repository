<template>
  <div class="car-details">
    <hr/>
    <div v-if='carDetails' class="wrapp-car-details">
      <h3>{{carDetails.brand}} {{carDetails.model}}</h3>
      <img  :src="carDetails.imgUrl" :alt="carDetails.brand + ' ' + carDetails.model"/>
      <p>Max speed this car: {{carDetails.maxSpeed}} km/h</p>
      <p>The year of entering the car on the market of Ukraine: {{carDetails.year}}</p>
      <div class="cheange-car-form">
        <h3>Change the characteristics of the car:</h3>
        <label for="carBrand">Car brand:</label>
        <input type="text" :value="carDetails.brand" id="carBrand" v-on:keyup="changeCarInfo($event.target.value, carDetails.id, 'brand')"/>
        <label for="carModel">Car model:</label>
        <input type="text" :value="carDetails.model" id="carModel" v-on:keyup="changeCarInfo($event.target.value, carDetails.id, 'model')"/>
        <label for="carMaxSpeed">Max speed:</label>
        <input type="text" :value="carDetails.maxSpeed" id="carMaxSpeed" v-on:keyup="changeCarInfo($event.target.value, carDetails.id, 'maxSpeed')"/>
        <label for="carYear">Year of production of the car:</label>
        <input type="text" :value="carDetails.year" id="carYear" v-on:keyup="changeCarInfo($event.target.value, carDetails.id, 'year')"/>
      </div>
    </div>
    <p v-else>Please select a car...</p>
  </div>
</template>

<script>
/* import axios from 'axios';  */

 export default {
  props:['carDetails'],
  
  methods: {
    changeCarInfo(changes, id,text){
      this.$emit('changeCarDetail', changes, id,text);
    }
  }
}

</script> 

<style scoped>
  
  .wrapp-car-details img{
    /*width: 300px;*/
    height: 200px;
  }
  .cheange-car-form input{
    display: block;
    margin-bottom: 20px;
  }
</style> 

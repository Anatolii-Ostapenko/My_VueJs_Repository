<template>
    <div class="cars-list">
        <h3>Car list</h3>
        <hr/>
        <div class="wrapp-list" v-for="(car, index) in cars" :key="index">
        <p  @click="showCarDetails(index)">{{index+1}}. {{car.brand}} {{car.model}} </p>
        <button @click="removeCar(index)">Remove this Car</button>
      </div>
    </div>
</template>

<script>
export default {
    props:['cars'],
    methods: {
        showCarDetails(index){
            this.$emit('selectCar', index)
        },
        removeCar(index){
            this.$emit('removeCar', index)
        }
    }
}
</script>

<style>
    .wrapp-list{
        display: flex;
        align-items: center
    }
    .wrapp-list p {
        font-weight: 600;
    }
    .wrapp-list button{
        height: 25px;
        font-weight: 600;
    }

</style>
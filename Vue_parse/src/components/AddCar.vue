<template>
    <div class="add-car">
        <div class="add-car-form">
            <form action="#">
                <h3>Add new car:</h3>
                <label for="carBrand">Car brand:</label>
                    <input type="text" v-model="carBrand" />
                <label for="carModel">Car model:</label>
                    <input type="text" v-model="carModel"  />
                <label for="carMaxSpeed">Max speed:</label>
                    <input type="text" v-model="carMaxSpeed"  />
                <label for="carYear">Year of production of the car:</label>
                    <input type="text" v-model="carYear"  />
                <button type="submit" @click="addCar">Add car</button>
            </form>
      </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            carBrand: '',
            carModel: '',
            carMaxSpeed: '',
            carYear: ''
        }
    },
    methods: {
        addCar(){
            let obj = {
                brand: this.carBrand,
                model: this.carModel,
                maxSpeed: this.carMaxSpeed,
                year: this.carYear
            }
            this.$emit('addCar', obj)
        }
    }
}
</script>
<style scoped>
    .add-car-form{
        display: flex;
        flex-direction: column;
        width: 200px;
    }
</style>
 

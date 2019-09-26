<template>
  <div id="app">
    <CarsList :cars="cars" @selectCar="selectCar" @removeCar="removeCar" />
    <CarDetails :carDetails="carDetails" @changeCarDetail="changeCarDetail"/>
    <AddCar @addCar="addCar" />
  </div>
</template>

<script>
import CarsList from './components/CarsList'
import CarDetails from './components/CarDetails';
import AddCar from './components/AddCar'


export default {
  components: {
    CarsList,
    CarDetails,
    AddCar
  },
  data() {
    return {
      cars : [
        {id: 0, brand: 'KIA', model: 'Rio', maxSpeed: 180, year: 2012, imgUrl: require('@/assets/kia-rio2012.png')},
        {id: 1, brand: 'BMW', model: 'M3', maxSpeed: 250, year: 2014, imgUrl: require('@/assets/bmw-m3.png')},
        {id: 2, brand: 'VOLVO', model: 'XC90', maxSpeed: 200, year: 2016, imgUrl: require('@/assets/volvo-xc90.png')},
        {id: 3, brand: 'Audi', model: 'A6', maxSpeed: 240, year: 2011, imgUrl: require('@/assets/audi-a6.png')},
        {id: 4, brand: 'Opel', model: 'Astra', maxSpeed: 190, year: 2017, imgUrl: require('@/assets/opel-astra.png')},
        {id: 5, brand: 'Citroen', model: 'C4', maxSpeed: 210, year: 2018, imgUrl: require('@/assets/citron-c4.png')}
      ],
      carDetails: null
    }
  },
  methods: {
    selectCar(index){
      this.carDetails = this.cars[index]
    },
    removeCar(index){
      //let tmp = [];
      /* for (let i = 0; i < this.cars.length; i++){
        if(this.cars[i].id != index){
          tmp.push(this.cars[i])
        }
      } */
      //test method filter()
      let tmp = this.cars.filter((item, i) => {
        if(i != index) return item
      })
      this.cars = tmp;
    },
    changeCarDetail(changes, id, selectFild){
      for(let i=0; i < this.cars.length; i++){
        if(i == id){
          this.cars[i][selectFild] = changes
        }
      }
    },
    addCar(obj){
      if(obj.brand == ''){
        alert('Plece input car brand')
      }
      else{
        obj.id = this.cars.length
        this.cars.push(obj)
      }
      
    }
  }
}
</script>



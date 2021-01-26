<template>
  <div class="container mt-5">
    <div class="row mb-3">
      <div class="col">
        <h1 class="title">Cars application</h1>
      </div>
    </div>
  </div>

  <div class="row">
    <div class="col-md-4">
      <div class="form-group">
        <label for="search">Find your car</label>
        <input type="text" 
        class="form-control" 
        id="search" 
        placeholder="Name, Model ..." 
        v-model="search"
        />
      </div>

      <hr />
      <ul class="list-group" >
        <li
          v-for="car in filteredCars"
          :key="car.id"
          class="list-group-item list-group-item-action pointer"
          @click="selectCar(car)"
          :class="{active: selectedCarIndex === car.id}"
        >
          {{ car.name }} - {{ car.model }}
        </li>
      </ul>
    </div>
    <car-details :car="car"></car-details>
  </div>
    
  
</template>

<script>
import CarDetails from './CarDetails'

const car = (id, name, model, price, owner, year, phone, image) => ({
  id,
  name,
  model,
  price,
  owner,
  year,
  phone,
  image
})

const cars = [
  car(0, 'BMW', 'M5 F90', '250.000', 'Max', 2020, '+7 489 934 77 89', 'BMW.jpg'),
  car(1, 'Nissan', 'GTR', '120.000', 'Angella', 2016, '+7 593 645 22 12', 'Nissan_GTR.jpg'),
  car(2, 'Mercedes', 'AMG GT63', '220.000', 'John', 2019, '+7 593 324 67 12', 'Mercedes.jpg'),
  car(3, 'BMW', 'M5 F10', '170.000', 'Tom', 2017, '+7 767 333 23 22', 'BMWf10.jpg'),
  car(4, 'Mitsubisi', 'Evo X', '130.000', 'Mark', 2015, '+8 875 637 13 82', 'Evo10.jpg'),
  car(5, 'Subaru', 'STI', '230.000', 'Bella', 2020, '+8 375 727 31 66', 'Subaru_STI.jpg')
]


export default {

  components: { CarDetails  },
  data() {
    return {
      cars: cars,
      car: cars[0],
      selectedCarIndex: 0,
      search: '',
    }
  },

  methods: {
    selectCar(car) {
      this.car = car
      this.selectedCarIndex = car.id
    },
  },

  computed: {
      filteredCars(){
        return this.cars.filter((car) => {
          return car.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1 
          || 
          car.model.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
    },
  }
}
</script>

<style scoped>
.row {
  margin-left: 30px;
}
.title {
  margin-left: 120px;
}
.list-group-item.active{
  background: rgb(63, 185, 132);
  color: rgb(52, 73, 94);
}
</style>

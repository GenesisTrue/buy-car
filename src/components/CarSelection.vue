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
        <input type="text" class="form-control" id="search" placeholder="Name, Model ..." />
      </div>

      <hr />
      <ul class="list-group">
        <li
          v-for="(car,index) in cars"
          v-bind:key="index"
          class="list-group-item list-group-item-action pointer"
          @click="selectCar(index)"
          :class="{ active: selectedCarIndex === index }"
        >{{ car.name }} - {{ car.model }}</li>
      </ul>
    </div>
    <car-details :car="car"></car-details>
  </div>
</template>

<script>
import CarDetails from "./CarDetails";

const car = (name, model, price, owner, year, phone, image) => ({
  name,
  model,
  price,
  owner,
  year,
  phone,
  image,
});

const cars = [
  car(
    "BMW",
    "M5 F90",
    "250.000",
    "Nodir",
    2020,
    "+7 489 934 77 89",
    "./images/BMW.jpg"
  ),
  car(
    "Nissan",
    "GTR",
    "120.000",
    "Angella",
    2016,
    "+7 593 645 22 12",
    "./images/Nissan_GTR.jpg"
  ),
  car(
    "Mercedes",
    "AMG GT63",
    "220.000",
    "John",
    2019,
    "+7 593 324 67 12",
    "./images/Mercedes.jpg"
  ),
];

export default {
  name: "CarSelection",
  components: { CarDetails },
  data() {
    return {
      cars: cars,
      car: cars[0],
      selectedCarIndex: 0,
    };
  },
  methods: {
    selectCar(index) {
      this.car = cars[index];
      this.selectedCarIndex = index;
    },
  },
};
</script>

<style scoped>
.row {
  margin-left: 30px;
}
.title {
  margin-left: 120px;
}
</style>


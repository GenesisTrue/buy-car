<template>
  <div class="container mt-5">
    <div class="row mb-3">
      <div class="col">
        <h1>Cars application</h1>
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
          v-for="(car,index) of cars"
          :key="index"
          class="list-group-item list-group-item-action pointer"
          @click="selectCar(index)"
          :class="{'active' : selectedCarIndex === index }"
        >{{car.name}} - {{car.model}}</li>
      </ul>
    </div>

    <div class="col-md-8">
      <div class="row">
        <div class="col-md-5">
          <h2>{{car.name}}</h2>
          <img :src="car.image" v-bind:alt="car.name" class="rounded detailed-car-image" />
        </div>

        <div class="col-md-7">
          <h5>Car details</h5>

          <ul>
            <li>
              Model -
              <strong>{{car.model}}</strong>
            </li>
            <li>
              Year -
              <strong>{{car.year}}</strong>
            </li>
            <li>
              Owner -
              <strong>{{car.owner}}</strong>
            </li>
            <li>
              Price -
              <strong>{{car.price}}$</strong>
            </li>
          </ul>

          <p v-if="phoneVisibility">{{car.phone}}</p>

          <button
            class="btn btn-outline-success mr-3"
            @click="phoneVisibility = !phoneVisibility"
          >Show phone</button>
          <button class="btn btn-primary">Buy</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
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
  name: "App",
  data() {
    return {
      cars: cars,
      car: cars[0],
      selectedCarIndex: 0,
      phoneVisibility: false,
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
.detailed-car-image {
  height: 200px;
}
.pointer {
  cursor: pointer;
}
</style>



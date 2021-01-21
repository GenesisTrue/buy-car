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
          v-for="(car,index) in cars"
          :key="index"
          class="list-group-item list-group-item-action pointer"
        >{{car.name}} - {{car.model}}</li>
      </ul>
    </div>
    <div class="col-md-8">
      <div class="row">
        <div class="col-md-5">
          <h2>BMW</h2>
          <img src="./assets/images/BMW.jpg" alt class="rounded detailed-car-image" />
        </div>

        <div class="col-md-7">
          <h5>Car details</h5>

          <ul>
            <li>
              model -
              <strong>BMW</strong>
            </li>
            <li>
              Year -
              <strong>2020</strong>
            </li>
            <li>
              Owner -
              <strong>John</strong>
            </li>
            <li>
              Price -
              <strong>250.000$</strong>
            </li>
          </ul>

          <p>+ 7 983 123 45 54</p>

          <button class="btn btn-outline-success mr-2">Show phone</button>
          <button class="btn btn-primary">Buy</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const cars = [
  {
    name: "BMW",
    model: "M5 F90",
    price: "250.000",
    owner: "Nodir",
    year: 2020,
    phone: "+7 489 934 77 89",
    image: "./assets/images/BMW.jpg",
  },
  {
    name: "Mersedes",
    model: "AMG GT63",
    price: "220.000",
    owner: "John",
    year: 2019,
    phone: "+7 593 324 67 12",
    image: "./assets/images/Mersedes.jpg",
  },
  {
    name: "Nissan",
    model: "GTR",
    price: "120.000",
    owner: "Angella",
    year: 2016,
    phone: "+7 593 645 22 12",
    image: "./assets/images/Nissan_GTR.jpg.jpg",
  },
];
export default {
  name: "App",
  data() {
    return {
      cars: cars,
    };
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


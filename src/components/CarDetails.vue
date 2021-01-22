<template>
  <div class="col-md-8">
    <div class="row">
      <div class="col-md-5 img-wrapper">
        <h2>{{ car.name }}</h2>
        <img :src="car.image" v-bind:alt="car.name" class="rounded detailed-car-image" />
      </div>
      <div class="col-md-7">
        <h5>Car details</h5>
        <ul>
          <li>
            Model -
            <strong>{{ car.model }}</strong>
          </li>
          <li>
            Year -
            <strong>{{ car.year }}</strong>
          </li>
          <li>
            Owner -
            <strong>{{ car.owner }}</strong>
          </li>
          <li>
            Price -
            <strong>{{ car.price }}$</strong>
          </li>
        </ul>
        <div class="phone-block">
          <p v-if="phoneVisibility">{{ car.phone }}</p>
        </div>

        <button
          class="btn btn-outline-success mr-3"
          @click="phoneVisibility = !phoneVisibility"
        >Show phone</button>
        <button class="btn btn-primary">Buy</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CarDetails",
  props: ["car"],
  data() {
    return {
      phoneVisibility: false,
    };
  },
};
</script>

<style >
.row {
  margin-left: 30px;
}

.detailed-car-image {
  height: 200px;
}
.pointer {
  cursor: pointer;
}
.img-wrapper {
  text-align: center;
}
.phone-block {
  height: 40px;
}
</style>


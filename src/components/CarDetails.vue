<template>
  <div class="col-md-8">
    <div class="row">
      <div class="col-md-5 img-wrapper">
        <h2>{{ car.name }} - {{ car.model }}</h2>
        <img :src="require('../assets/images/' + car.image) " v-bind:alt="car.name" class="rounded detailed-car-image" />
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

        <button class="btn btn-outline-success mr-3" @click="phoneVisibility = !phoneVisibility">
          {{ phoneBtnText }}
        </button>
        <button class="btn btn-primary" @click="showModal = true">Buy</button>
      </div>
    </div>
  <logs :car="car" ref="CustomLog" ></logs>

  </div>

  <modal @modalStatus="modalStatus" v-if="showModal" :car="car"/>

</template>

<script>
import Modal from './Modal'
import logs from './Logs'

export default {
  components: { Modal , logs},
  name: 'CarDetails',
  props: ['car'],
  data() {
    return {
      phoneVisibility: false,
      showModal: false
    }
  },

  methods: {

    modalStatus(val) {

      if(val == 'buy'){
        this.showModal = false
        this.$refs.CustomLog.confirmOrder()

      }else if (val == 'close'){
        this.showModal = false
        this.$refs.CustomLog.cancelOrder()
      }
    },

    
  },

  computed: {
    phoneBtnText() {
      return this.phoneVisibility ? 'Hide phone' : 'Show phone'
    },
  }
}
</script>

<style>
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

<template>
  <div class="row" v-if="logs.length" >
    <div class="col-md-12 log">
      <ul class="list-group">
        <li 
        v-for="(log,index) in logs"
        :key="index"
        class="list-group-item"
        :class="{
          'list-group-item-secondary': log.type === 'cnl',
          'list-group-item-light': log.type === 'ok'
        }"
        >
         <strong class="title">{{ log.text }}</strong> <br> {{ log.date }}
        </li>
      </ul>
    </div>
  </div>
</template>
<script>

const log = (text, type, date = new Date().toLocaleString()) => ({text, type, date})
export default {
  name: 'Logs',
  props: ['car'],
  data(){
    return {
      logs: []
    }
  },
  methods: {
    confirmOrder() {
      this.logs.push(
        log(`Seccess Order: ${this.car.name} - ${this.car.model}`, 'ok')
      )
    },
    cancelOrder() {
      this.logs.push(
        log(`Cancel Order: ${this.car.name} - ${this.car.model}`, 'cnl')
      )
    },
  },
}
</script>

<style scoped>
.log {
  padding-left: 30px;
  padding-top: 50px;
  max-width: 41.666667%;
}
.log .list-group-item-light{
  background: rgb(63, 185, 132);
}
strong.title{
  color: rgb(52, 73, 94);
}
</style>
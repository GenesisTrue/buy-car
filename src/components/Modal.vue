<template>
  <div class="modal fade show" tabindex="-1" role="dialog" >
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Do you want to boy this car?</h5>
          <button 
          type="button" 
          class="close" 
          data-dismiss="modal" 
          aria-label="Close"
           @click="$emit('closeModal')"
          >
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">
          <p>Current Car - <strong>{{car.name}}</strong></p>

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
        </div>

        <div class="modal-footer">
          <button type="button" class="btn btn-primary" @click="$emit('modalStatus', 'buy')" >Buy</button>
          <button 
          type="button" 
          class="btn btn-secondary" 
          data-dismiss="modal"
          @click="$emit('modalStatus','close')"
          >
          Close
          </button>
        </div>
      </div>
    </div>
  </div>
  <div class="modal-backdrop fade show" ></div>
  
</template>

<script>
export default {
  name: 'modal',
  props: ['car'],
  emits: ["modalStatus"]
}
</script>

<style scoped>
.modal {
  display: block;
}
</style>
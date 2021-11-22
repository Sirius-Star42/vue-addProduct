<template>
  <div class="col-md-3 p-4" style="background-color: white">
    <div class="form-group" style="display: flex; flex-direction: column;">
      <label for="my-textarea">Add Product Quantity</label>
      <textarea
        v-model="quantity"
        id="my-textarea"
        class="form-control"
        name=""
        rows="1"
        placeholder="Product quantity to add"
      ></textarea>
      <button @click="addQuantity" class="btn btn-outline-primary mt-3">Add</button>
    </div>
  </div>
</template>
<script>
import {eventBus} from '../main'

export default {
  data() {
    return {
      quantity: null
    }
  },
  methods: {
    addQuantity() {
      eventBus.$emit("addedQuantity", this.quantity)
    }
  }
}
</script>
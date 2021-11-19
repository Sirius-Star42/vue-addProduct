<template>
  <div class="row product-container">
    <app-product v-for="product in productsList" :key="product.index">
      <img
        class="card-img-top"
        :src="product.selectedImage"
        :alt="product.title"
      />
      <div class="card-body">
        <h5 class="card-title">{{ product.title }}</h5>
        <small> <strong>Adet : </strong>{{ product.count }}</small>
        <br />
        <small> <strong>Fiyat : </strong>{{ product.price }}</small>
        <br />
        <small> <strong>Tutar : </strong>{{ product.totalPrice }}</small>
      </div>
    </app-product>
  </div>
</template>
<script>
import Product from "./Product.vue";
import { eventBus } from "../main";

export default {
  components: {
    appProduct: Product,
  },
  data() {
    return {
      productsList: [],
    };
  },
  created() {
    eventBus.$on("productAdded", (product) => {
      if (this.productsList.length < 2) { 
        this.productsList.push(product);
        eventBus.$emit("progressBarUpdated", this.productsList.length)
      } else {
        alert("It can not be added product more than 2");
      }
    });
  },
};
</script>
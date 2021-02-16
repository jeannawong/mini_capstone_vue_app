<template>
  <div class="home">
    <h1>All Pet Rocks</h1>
    <div v-for="product in products" v-bind:key="product.id">
      <h2>{{ product.name }}</h2>
      <img v-bind:src="product.primary_image_url" v-bind:alt="product.name" />
      <!-- <p>Width: {{ photo.width }}</p> -->
      <!-- <p>Height: {{ photo.height }}</p> -->
    </div>
  </div>
</template>

<style scoped>
img {
  height: 150px;
  width: auto;
}
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      products: [],
    };
  },
  created: function() {
    this.indexProducts();
  },
  methods: {
    indexProducts: function() {
      axios.get("/api/products").then(response => {
        console.log("products index", response);
        this.products = response.data;
      });
    },
  },
};
</script>

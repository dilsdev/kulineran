<template>
  <div class="home">
    <NavbarComponen />
    <div class="container">
      <HeroComponen />
    <div class="row mt-4">
      <div class="col">
        <h2>Best <strong>Food</strong></h2>
      </div>
      <div class="col">
        <router-link to="/foods" class="btn btn-success float-end">Lihat semua</router-link>
      </div>
    </div>
    <div class="row mb-3">
      <div class="col-md-4 mt-4" v-for="product in products" :key="product.id">
        <CardProduct :product="product"/>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import NavbarComponen from "@/components/NavbarComponen.vue";
import HeroComponen from "@/components/HeroComponen.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from 'axios'

export default {
  name: "HomeView",
  components: {
    NavbarComponen,
    HeroComponen,
    CardProduct
  },
  data() {
    return {
      products : [],
    }
  },
  methods: {
  setProduct(data) {
      this.products = data
    }
  },
  mounted() {
    axios.get('http://localhost:3000/best-products')
      .then((response)=> {
        // handle success
        this.setProduct(response.data)
    });
   }
};
</script>

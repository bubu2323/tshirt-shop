<script>
import ProductDisplay from "./components/ProductDisplay.vue";
import NavbarTop from "./components/NavbarTop.vue";

export default {
  components: { ProductDisplay, NavbarTop },
  data() {
    return {
      cart: [],
      premium: false,
      notAvailableError: false,
    };
  },
  methods: {
    incrementChart(availability, product) {
      this.notAvailableError = false;
      //add clicked elem details to chart
      let elem = { id: product.id, name: product.product };
      //prettier-ignore
      return availability ? this.cart.push(elem):(this.notAvailableError = true);
    },
  },
};
</script>
<!-- /*html*/ -->
<template>
    <NavbarTop :premium="premium" @addToCartElem="incrementChart" :cart="cart"></NavbarTop>
  <div class="container">

  
  
    <div v-if="notAvailableError" class="alert alert-danger" role="alert">
      Not possible to add to cart, product out of stock. Select another one.
    </div>
    <div class="product-display">
      <!-- <div class="cart">
        <p>Cart products:{{ cart.length }}</p>
      </div> -->
      <ProductDisplay :premium="premium" @addToCartElem="incrementChart">
      </ProductDisplay>
      
    </div>
  </div>
</template>

<style></style>

<script>
export default {
  props: ["cart"],
  data() {
    return {
      // myCart: this.cart
    };
  },
  methods: {},
};
</script>
<template>
  <nav class="">
    <ul class="">
      <li>
        <a class="text-logo" href="#"
          ><img id="logo" src="/src/assets/img/logo.png" alt="" />E-Shoes</a
        >
      </li>
      <!-- cart -->
      <li class="cart-li">
        <button type="button" class="btn btn-success position-relative">
          <i class="fa-solid fa-cart-shopping fa-lg"></i>
          <span
            class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger num-cart"
          >
            {{ cart.length }}
          </span>
        </button>
      </li>
    </ul>
  </nav>
</template>
<style>
.text-logo {
  text-decoration: none;
  font-size: 1.3em;
  color: black;
}
#logo {
  font-size: 2em;
  width: 2em;
}
nav {
  background-color: rgb(220, 220, 220);
}
li {
  display: inline;
}
ul {
  padding-top: 0.5em;
  padding-bottom: 0.5em;
}
li a.navbar-link {
  float: right;
  text-decoration: none;
  font-size: 1.2em;
}
li.cart-li {
  float: right;
  margin-top: 0;
  margin-right: 2em;
  padding: 1em;
  /* border: 1px solid rgb(103, 100, 100); */
}
a.navbar-link:hover {
  color: black;
  padding: 0.2em;
  background-color: rgb(169, 189, 169);
}
</style>

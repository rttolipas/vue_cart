<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col">
          <div class="row">
            <div class="col sm-6" v-for="product in products" :key="product.id">
              <product
                v-bind:moneyFormat="moneyFormat"
                v-bind:isInCart="isInCart"
                v-on:add-to-cart="addToCart"
                v-bind:product="product"
              ></product>
            </div>
          </div>
        </div>
        <div class="col col-4">
          <cart
            v-bind:items="cart"
            v-bind:moneyFormat="moneyFormat"
            v-on:remove-from-cart="removeFromCart"
            v-on:pay-now="payNow"
          ></cart>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import products from "@/products.json";
import Product from "@/components/Product.vue";
import Cart from "@/components/Cart.vue";
export default {
  name: "app",
  components: {
    Product,
    Cart
  },
  data() {
    return {
      products,
      cart: []
    };
  },
  methods: {
    addToCart(product) {
      this.cart.push(product);
    },
    removeFromCart(product) {
      this.cart = this.cart.filter(item => item.id !== product.id);
    },
    isInCart(product) {
      return this.cart.find(item => item.id === product.id);
    },
    moneyFormat(amount) {
      return "P" + Number(amount).toFixed(2);
    },
    payNow(total) {
      this.cart = [];
      alert("Shopping completed!");
    }
  }
};
</script>

<style>
body {
  background-color: #eee;
}
</style>

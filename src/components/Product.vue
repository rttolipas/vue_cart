<template>
  <div class="card my-5 bg-warning p-3" style="width: 20rem;">
    <img class="card-img-top" :src="product.image">
    <div class="card-body">
      <h5 class="text-center card-title">{{ product.title }}</h5>
      <p class="text-center text-muted">
        <code>{{ moneyFormat(product.price) }}</code>
      </p>
      <button
        v-bind:disabled="isInCart(product)"
        @click="$emit('add-to-cart', product)"
        class="btn btn-primary form-control"
      >{{ isInCart(product) ? 'Added to Cart' : 'Add to Cart' }}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: ["product", "isInCart", "moneyFormat"]
};
</script>

<style>
</style>

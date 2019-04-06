<template>
  <div>
    <div class="card p-3 my-5">
      <div class="card-title">
        <small>Total Payment:</small>
      </div>
      <div class="card-body text-center">
        <h1>{{ moneyFormat(total) }}</h1>
      </div>
    </div>

    <ul class="list-group">
      <li class="list-group-item" v-for="item in items" :key="item.id">
        {{ item.title }} -
        <code>{{ moneyFormat(item.price) }}</code>
        <button
          @click="$emit('remove-from-cart', item)"
          class="btn badge badge-danger float-right"
        >Remove</button>
      </li>
    </ul>

    <button
      :disabled="total===0"
      @click="$emit('pay-now')"
      class="btn btn-success form-control my-3"
    >Pay Now</button>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: ["items", "moneyFormat"],
  computed: {
    total() {
      return this.items.reduce((acc, item) => acc + Number(item.price), 0);
    }
  }
};
</script>

<style>
</style>

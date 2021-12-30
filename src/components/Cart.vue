<template>
  <div class="cart">
    <h2>Your Cart</h2>
    <p v-show="!products.length">
      <i>Please add some products to cart.</i>
    </p>
    <ul>
      <li v-for="product in products" :key="product.id">
        {{ product.title }} - {{ currency(product.price) }} x
        {{ product.quantity }}
      </li>
    </ul>
    <p>Total: {{ currency(total) }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import CartO from "@/types/CartO";
import { currency } from "../currency";
export default defineComponent({
  name: "Cart",
  props: {
    products: {
      required: true,
      type: Array as PropType<CartO[]>,
    },
    total: {
      required: true,
      type: Number,
    },
  },
  setup() {
    return {
      currency,
    };
  },
});
</script>

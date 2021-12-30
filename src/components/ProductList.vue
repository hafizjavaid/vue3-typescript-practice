<template>
  <ul>
    <li v-for="product in products" :key="product.id">
      {{ product.title }} - {{ currency(product.price) }}
      <button :disabled="!product.inventory" @click="addProductToCart(product)">
        Add to cart
      </button>
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Product from "@/types/Product";
import { currency } from "../currency";

export default defineComponent({
  name: "ProductList",
  props: {
    products: {
      required: true,
      type: Array as PropType<Product[]>,
    },
  },
//   emits: ["addProductToCart"],
  setup(_, { emit }) {
    const addProductToCart = (product: Product) => {
      emit("addProductToCart", product);
    };
    return {
      currency,
      addProductToCart,
    };
  },
});
</script>

<style>
ul {
  list-style: none;
}
li {
  display: flex;
  margin: 10px auto;
  justify-content: space-between;
  align-items: center;
}
</style>

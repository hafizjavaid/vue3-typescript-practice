<template>
  <div class="app">
    <h1>Shopping Cart</h1>
    <div class="products">
      <h2>Product</h2>
      <product-list
        :products="products"
        @addProductToCart="addProductToCart"
      ></product-list>
    </div>
    <div class="cart">
      <h2>Cart</h2>
      <cart :products="cartItems" :total="total"></cart>
    </div>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, ref } from "vue";
import Cart from "./components/Cart.vue";
import ProductList from "./components/ProductList.vue";
import Product from "./types/Product";
import CartO from "./types/CartO";

export default defineComponent({
  name: "App",
  components: { ProductList, Cart },
  setup() {
    const products = ref<Product[]>([
      { id: 1, title: "iPad 4 Mini", price: 500.01, inventory: 2 },
      { id: 2, title: "H&M T-Shirt White", price: 10.99, inventory: 10 },
      { id: 3, title: "Charli XCX - Sucker CD", price: 19.99, inventory: 5 },
    ]);
    const cartItems = ref<CartO[]>([]);
    const total = computed(() => {
      if (cartItems.value.length > 0) {
        return cartItems.value.reduce(
          (total: number, product: CartO): number => {
            return total + product.price * product.quantity;
          },
          0
        );
      } else {
        return 0;
      }
    });
    return {
      products,
      cartItems,
      total,
    };
  },
  methods: {
    addProductToCart(product: Product) {
      console.log(JSON.stringify(product));
      // product = JSON.parse(product)
      if (product.inventory > 0) {
        const cartItem = this.cartItems.find((item) => item.id === product.id);
        if (!cartItem) {
          this.pushProductToCart(product);
        } else {
          this.incrementItemQuantity(product);
        }
        this.updateInventory(product);
      }
    },
    pushProductToCart(product: Product) {
      this.cartItems.push({
        ...product,
        quantity: 1,
      });
    },
    incrementItemQuantity(product: Product) {
      this.cartItems = [...this.cartItems].map((item) => {
        if (item.id === product.id) {
          item.quantity++;
        }
        return item;
      });
    },
    updateInventory(product: Product) {
      this.products = [...this.products].map((item) => {
        if (item.id === product.id) {
          if (item.inventory > 0) {
            item.inventory--;
          } else {
            item.inventory = 0;
          }
        }
        return item;
      });
    },
  },
});
</script>

<style></style>

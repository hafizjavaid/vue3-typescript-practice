<template>
  <div class="app">
    <p>{{ name }} - {{ age }}</p>
    <button @click="changeAge(30)">changeAge</button>
    <button @click="changeName('Javaid')">changeName</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
  components: {},
  data() {
    return {
      name: "Hafiz" as string,
      age: 25 as number | string,
    };
  },
  methods: {
    changeAge(age: number | string) {
      this.age = age;
    },
    changeName(name: string) {
      this.name = name;
    },
  },
});
</script>

<style></style>

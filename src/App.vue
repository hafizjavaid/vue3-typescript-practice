<template>
  <div class="app">
    <!-- ============ Basics ============== -->
    <!-- <p>{{ name }} - {{ age }}</p>
    <button @click="changeAge(30)">changeAge</button>
    <button @click="changeName('Javaid')">changeName</button> -->
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import Job from "./types/Job";
export default defineComponent({
  name: "App",
  components: {},

  setup() {
    const jobs = ref<Job[]>([
      {
        title: "farm worker",
        location: "lon lon ranch",
        salary: 30000,
        id: "1",
      },
      {
        title: "quarryman",
        location: "death mountain",
        salary: 40000,
        id: "2",
      },
      {
        title: "flute player",
        location: "the lost woods",
        salary: 35000,
        id: "3",
      },
      { title: "fisherman", location: "lake hylia", salary: 21000, id: "4" },
      {
        title: "prison guard",
        location: "gerudo valley",
        salary: 32000,
        id: "5",
      },
    ]);

    return {
      jobs,
    };
  },

  // Basics Container (Use Typescript and Composition API)
  //   {
  // // Vue-3 but with Reactive
  //   // setup() {
  //     // +++++++++++++++++++++++++++++++++++++++ Basics ++++++++++++++++++++++
  //     // ============== Vue-3 but with Reactive ==============
  //     // const state = reactive({
  //     //   name: "Hafiz" as string,
  //     //   age: 25 as number | string,
  //     // });

  //     // // To update within the state
  //     // state.name = "Javaid";

  //     // return {
  //     //   ...toRefs(state),
  //     // };
  //     // ============== Vue-3 but with Ref ==============
  //     // const name = ref("Hafiz");
  //     // const age = ref<string | number>("Hafiz");
  //     // // For updating Purpose
  //     // name.value = "Javaid";
  //     // return {
  //     //   name,
  //     //   age,
  //     // };
  //   // },

  //   // Vue2 things
  //   // data() {
  //   //   return {
  //   //     name: "Hafiz" as string,
  //   //     age: 25 as number | string,
  //   //   };
  //   // },

  //   // It will work fine with reactive
  //   // methods: {
  //   //   changeAge(age: number | string) {
  //   //     this.age = age;
  //   //   },
  //   //   changeName(name: string) {
  //   //     this.name = name;
  //   //   },
  //   // },

  //   // +++++++++++++++++++++++++++++++++++++++ Basics ++++++++++++++++++++++
  //   }
});
</script>

<style></style>

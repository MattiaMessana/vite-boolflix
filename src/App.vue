<script>
  import { store } from "./store";
  import axios from "axios";
  import MyHeader from "./components/MyHeader.vue";
  import MyMain from "./components/MyMain.vue";

  export default {
    components: {
        MyHeader,
        MyMain,
    },
    data() {
      return {
        store,

      };
    },
  }

</script>

<template>

  <MyHeader />
  <MyMain />

</template>

<style lang="scss">

</style>
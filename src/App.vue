<script>
  import { store } from "./store";
  import axios from "axios";
  import MyHeader from "./components/MyHeader.vue";
  import MyCardsList from "./components/MyCardsList.vue";

  export default {
    components: {
        MyHeader,
        MyCardsList,
    },
    data() {
      return {
        store,
      };
    },
    created() {
      this.getCards();
      
    },
    methods: {
      getCards() {
        const paramsObj = {
        api_key: "4de0eca76da6b34f96ce4baecfb99307",
        query: this.store.query,
      }
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: paramsObj,
        })
        .then((resp) => {
          console.log(resp.data.results);
          this.store.movieList = resp.data.results;
        })
      }
    }
  }

</script>

<template>

  <MyHeader @search="getCards"/>
  <MyCardsList :cardsArray="store.movieList" />

</template>

<style lang="scss">

</style>
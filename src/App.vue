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
      this.getAllCards();
    },
    methods: {
      getCards(type = 'tv') {
        const paramsObj = {
        api_key: "4de0eca76da6b34f96ce4baecfb99307",
        query: this.store.query,
        flags: ["en" , "it" , "es" , "de" , "ja", "fr", "pt"],
      }

      axios
        .get("https://api.themoviedb.org/3/search/" + type, {
          params: paramsObj,
        })
        .then((resp) => {
          console.log(resp.data.results);
          if (type === 'movie') {
            this.store.movieList = resp.data.results;
          } else {
            this.store.tvList = resp.data.results;
          }
          this.store.query = "";

        })
      },
      getAllCards() {
        console.log("ciao");
        this.getCards('movie');
        this.getCards('tv');
      }

    },
  }

</script>

<template>

  <MyHeader @search="getAllCards"/>

  <div class="container p-3">

    <h2 class="text-light">MOOVIES</h2>
    <MyCardsList :cardsArray="store.movieList" />
    <h2 class="text-light mt-5">TV SERIES</h2>
    <MyCardsList :cardsArray="store.tvList" />

  </div>


</template>

<style lang="scss">
  a {
    cursor: pointer;
  }
</style>
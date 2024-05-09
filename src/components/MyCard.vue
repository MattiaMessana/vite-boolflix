<script>
export default {
    props: {
        cardObj: Object,
    },
    data() {
        return {
            flags: ["en" , "it" , "es" , "de" , "ja", "fr"],
        };
    },
    methods: {
        getImagePath(imageName) {
            return new URL(`../assets/img/${imageName}.png`, import.meta.url).href;
        },
        hasFlags() {
            console.log("ciao");
            if (this.flags.includes(this.cardObj.original_language) ) {
                return true;
            } else {
                return false;
            }
        }

    }
}
</script>

<template>
    
    <!-- creiamo singola carta  -->
    <div class="card mt-4 p-3 border-0">

        <img :src=" `https://image.tmdb.org/t/p/w342/` + `${cardObj.poster_path}`"  class="card-img-top" :alt="cardObj.original_title">

        <div class="card-body">
            <h5 class="card-title mb-4"> {{cardObj.title}}</h5>
            <p class="card-subtitle"> {{cardObj.original_title}} </p>

            <img v-if="hasFlags()" class=" mb-2 mt-2" :src="getImagePath(cardObj.original_language)" alt="">
            <p v-else class="card-subtitle"> {{cardObj.original_language}} </p>

            <p class="card-subtitle"> {{cardObj.vote_average}} </p>
        </div>

    </div>

</template>

<style scoped lang="scss">

    card-body {
        img {
            width: 30px;
        }
    }

</style>
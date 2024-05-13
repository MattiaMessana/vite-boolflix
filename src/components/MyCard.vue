<script>
export default {
    props: {
        cardObj: Object,
    },
    data() {
        return {
            flags: ["en" , "it" , "es" , "de" , "ja", "fr", "pt"],
        };
    },
    methods: {
        getImagePath(imageName) {
            return new URL(`../assets/img/${imageName}.png`, import.meta.url).href;
        },
        hasFlags() {
            if (this.flags.includes(this.cardObj.original_language) ) {
                return true;
            } else {
                return false;
            }
        },
        changeVote() {
            const vote = Math.round((this.cardObj.vote_average) / 2);
            return vote
        }
    }
}
</script>

<template>
    
    <!-- creiamo singola carta  -->
    <div class="card mt-4 p-3 border-0 text-bg-dark">

        <img v-if="!!cardObj.poster_path" :src=" `https://image.tmdb.org/t/p/w185/` + `${cardObj.poster_path}`"  class="card-img-top" :alt="cardObj.original_title">

        <img v-else src="https://www.altavod.com/assets/images/poster-placeholder.png" alt="">

        <div class="card-body">
            <h5 class="card-title mb-4"> {{cardObj.title}} {{cardObj.name}}</h5>
            <p class="card-subtitle"> {{cardObj.original_title}} {{cardObj.original_name}} </p>

            <img v-if="hasFlags()" class=" mb-2 mt-2" :src="getImagePath(cardObj.original_language)" alt="">
            <p v-else class="card-subtitle"> {{cardObj.original_language}} </p>

            <p class="card-subtitile">
                <i class="fa-solid fa-star" v-for="x in changeVote()"></i>
                <i class="fa-regular fa-star" v-for="x in (5 - changeVote())"></i>
            </p>
        </div>

    </div>

</template>

<style scoped lang="scss">
    .card-body {
        display: none;
        img {
            width: 30px;
            
        }
    }
    
    .card:hover .card-body {
        display: block;
    }
</style>
<script>
export default {
    props: {
        cardObj: Object,
    },
    data() {
        return {

        };
    },
}
</script>

<template>
    
    <!-- creiamo singola carta  -->
    <div class="card mt-4 p-3 border-0">

        <!-- <img :src="cardObj.image" class="card-img-top rounded-circle" alt="..."> -->

        <div class="card-body">
            <h5 class="card-title mb-4"> {{this.cardObj.title}}</h5>
            <p class="card-subtitle"> {{this.cardObj.original_title}} </p>
            <p class="card-subtitle"> {{this.cardObj.original_language}} </p>
            <p class="card-subtitle"> {{this.cardObj.vote_average}} </p>
        </div>
    </div>

</template>

<style scoped lang="scss">

</style>
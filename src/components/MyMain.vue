<script>
 import { store } from "../store";
 import MyCardsList from "./MyCardsList.vue";

export default {
    components: {
        MyCardsList,

    },
    data() {
        return {
            store,
        };
    },
}
</script>

<template>
    <div class="container">

        <!-- qui inseriremo la lista delle carte -->
        <MyCardsList />
        <p>CONTENT HERE</p>

    </div>    
</template>


<style scoped lang="scss">

</style>
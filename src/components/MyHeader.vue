<script>
    import { store } from "../store";

    export default {
        data() {
            return {
                store,
            };
        },
        methods: {
            
        }
    }

</script>

<template>

    <nav class="navbar bg-dark mb-3">
        <div class="container-fluid">
            <a class="navbar-brand link-danger fs-3 ">BOOFLIX</a>

            <form class="d-flex" role="search">
                <input  @keyup.enter="$emit('search')" v-model="store.query" class="form-control-sm me-2 rounded-4 border-0" type="search" placeholder="Search" aria-label="Search">
                <button @click.prevent="$emit('search')"  class="btn btn-dark"><i class="fa-solid fa-magnifying-glass"></i></button>
                <!-- il form riavvia la pagina quindi per evitare che si riavvii utilizziamo .prevent  -->
            </form>
        </div>
    </nav>

</template>

<style scoped lang="scss">

</style>
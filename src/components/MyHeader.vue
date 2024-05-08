<script>
    import { store } from "../store";

    export default {
        data() {
            return {
                store,
            };
        },
    }

</script>

<template>

    <nav class="navbar bg-dark mb-3">
        <div class="container-fluid">
            <a class="navbar-brand link-danger fs-3 ">BOOFLIX</a>
            <form class="d-flex" role="search">
            <input class="form-control-sm me-2 rounded-4 border-0" type="search" placeholder="Search" aria-label="Search">
            <button class="btn btn-dark" type="submit">GO</button>
            </form>
        </div>
    </nav>

</template>

<style scoped lang="scss">

</style>
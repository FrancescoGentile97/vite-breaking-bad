
<template>
    <main class="p-4">
        <div class="row row-cols-1 row-cols-lg-5 g-4">
            <div v-for="item in store.charactersList" class="col">
                <div class="card">
                    <img :src="item.image" class="img-fluid">
                    <h5>{{item.name}}</h5>
                    <p>{{item.status}}</p>
                </div>
            </div>

            </div>
    </main>


</template>

<style lang="scss">

</style>

<script>
import axios from "axios";
import { store } from "../store";

export default {
    data() {
        return {
            store,
        }

    },

    created() {
        axios.get("https://rickandmortyapi.com/api/character")
            .then((resp) => {
                console.log(resp);
                this.store.charactersList = resp.data.results;
            })
    }
}

</script>

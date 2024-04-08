<script>
import WordsList from '../words/WordsList.vue';
import Search from '../Search.vue';
import axios from 'axios';
const endpoint = 'http://localhost:8000/api/words/';

export default {
    name: 'HomePage',
    components: { WordsList, Search },
    data: () => ({ words: [], isLoading: false }),
    methods: {
        fetchWords() {
            this.isLoading = true;
            axios.get(endpoint).then(res => {
                this.words = res.data;
            }).catch(err => {
                console.error(err);
            }).then(() => {
                this.isLoading = false;
            })
        },

        async fetchApi(query) {
            this.isLoading = true;
            await axios.get(endpoint + query).then(res => {
                this.words = res.data;
            }).catch(err => {
                console.error(err);
            }).then(() => {
                this.isLoading = false;
            })
        }


    },
    created() {
        this.fetchWords();
    }
};
</script>

<template>
    <div class="d-flex justify-content-between align-items-center">
        <h1>Glossario</h1>
        <Search @search="fetchApi" />
    </div>
    <AppLoader v-if="isLoading" />
    <WordsList v-else :words="words" />

</template>

<style></style>
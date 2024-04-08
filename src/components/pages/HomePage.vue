<script>
import WordsList from '../words/WordsList.vue';
import Search from '../Search.vue';
import axios from 'axios';
const endpoint = 'http://localhost:8000/api/words/';

export default {
    name: 'HomePage',
    components: { WordsList, Search },
    data() {
        return {
            words: [],
            isLoading: false,
        };
    },
    methods: {
        fetchWords(searchTerm = '') {
            this.isLoading = true;
            axios.get(endpoint, { params: { q: searchTerm } })
                .then(res => {
                    this.words = res.data;
                })
                .catch(err => {
                    console.error(err);
                })
                .finally(() => {
                    this.isLoading = false;
                });
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
        <Search @search="fetchWords" />
    </div>
    <AppLoader v-if="isLoading" />
    <WordsList v-else :words="words" />
</template>

<style></style>

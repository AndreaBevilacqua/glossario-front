<script>
import WordsList from '../words/WordsList.vue';
import axios from 'axios';
const endpoint = 'http://localhost:8000/api/words/';

export default {
    name: 'HomePage',
    components: { WordsList },
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
        }
    },
    created() {
        this.fetchWords();
    }
};
</script>

<template>
    <h1>Glossario</h1>
    <AppLoader v-if="isLoading" />
    <WordsList v-else :words="words" />
</template>

<style></style>
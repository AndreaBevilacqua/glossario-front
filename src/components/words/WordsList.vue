<script>
import WordCard from './WordCard.vue';

export default {
    name: 'ProjectsList',
    components: { WordCard },
    props: { words: Array }
};
</script>

<template>
    <section id="words-list">
        <div v-if="words.length">
            <WordCard v-for="word in words" :key="word.id" :word="word" />
        </div>
        <h4 v-else>Non ci sono proggetti</h4>
    </section>
</template>


<style></style>
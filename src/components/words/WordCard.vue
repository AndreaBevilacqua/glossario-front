<script>
export default {
    name: 'WordCard',
    props: { word: Object },
    computed: {
        abstract() {
            const abstract = this.word.definition.slice(0, 550);
            return abstract + '...';
        },
        pubblicationDate() {
            const date = new Date(this.word.created_at);

            const day = date.getDate();
            const month = date.getMonth() + 1;
            const year = date.getFullYear();
            const hours = date.getHours();
            const minutes = date.getMinutes();
            // const seconds = date.getSeconds();

            return `${day}/${month}/${year} alle ${hours}:${minutes}`;
        }
    }
};
</script>

<template>
    <div class="card mt-3 mb-5">
        <div class="card-header d-flex justify-content-between align-items-center">
            <h2>{{ word.term }}</h2>
            <!-- <RouterLink v-if="!isDetail" :to="{ name: 'word-detail', params: { id: word.id } }"
                class="btn btn-primary">Vedi
            </RouterLink> -->
        </div>
        <div class="card-body clearfix">
            <p>{{ word.definition ? word.definition : abstract }}</p>
        </div>
        <div class="card-footer d-flex justify-content-between">
            <small>Pubblicato il {{ pubblicationDate }}</small>
        </div>
    </div>
</template>


<style></style>
<script>
export default {
    name: 'Search',
    data: () => ({ inputValue: '', timeoutId: null }),
    methods: {
        search() {
            clearTimeout(this.timeoutId);
            this.timeoutId = setTimeout(() => { this.$emit('search', this.inputValue); }, 500);
        }
    }
};
</script>

<template>
    <input type="text" placeholder="Cerca una parola" v-model="inputValue" @keyup="search" />
</template>

<style></style>
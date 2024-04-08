<script>
export default {
    name: 'Search',
    data() {
        return {
            inputValue: '',
            timeoutId: null
        };
    },
    methods: {
        search() {
            clearTimeout(this.timeoutId);
            this.timeoutId = setTimeout(() => {
                this.$emit('search', this.inputValue.trim());
            }, 1000);
        },
    }
};
</script>

<template>
    <input type="text" placeholder="Cerca una parola" v-model="inputValue" @keyup="search" />
</template>

<style></style>

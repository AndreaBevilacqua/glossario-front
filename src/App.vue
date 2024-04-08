<script>
import AppHeader from './components/AppHeader.vue';


export default {
  name: 'Glossario',
  components: { AppHeader },

};
</script>

<template>
  <AppHeader />
  <main class="container py-4">
    <RouterView />
  </main>
</template>

<style></style>
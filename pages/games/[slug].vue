<script setup>
import { useRoute } from 'vue-router';

const route = useRoute();
const slug = route.params.slug;
</script>

<template>
  <div>
    <h1 class="text-2xl font-bold">Game: {{ slug }}</h1>
    <p>This is the game details page for {{ slug }}.</p>
  </div>
</template>

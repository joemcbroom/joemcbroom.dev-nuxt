<script setup>
definePageMeta({
  title: 'Resume',
});

const { data } = await useFetch('/api/about');
</script>

<template>
  <p>
    <div v-if="data">{{ data }}</div>
  </p>
</template>

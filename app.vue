<template>
  <NuxtLayout name="main" :bgImage="bgImage" :class="backgroundColor">
    <NuxtPage />
  </NuxtLayout>
</template>

<style>
body {
  @apply text-zinc-900 dark:text-zinc-50;
}

.page-enter-from {
  opacity: 0;
  transform: translateX(100%);
}

.page-enter-active,
.page-leave-active {
  transition: all 0.2s;
}
.page-enter,
.page-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}
</style>

<script setup>
import gradients from '~/constants/gradients';

const route = useRoute();
const bgImage = ref(null);
const backgroundColor = ref(null);

watch(
  route,
  (newRoute) => {
    bgImage.value = newRoute?.meta?.backgroundImage || null;

    switch (newRoute.name) {
      case 'resume':
        backgroundColor.value = gradients[1];
        break;
      case 'contact':
        backgroundColor.value = gradients[2];
        break;
      default:
        backgroundColor.value = gradients[0];
        break;
    }
  },
  { immediate: true }
);
</script>

<script setup>
import { computed, onMounted, ref } from 'vue';
import sunUrl from '/img/sun.svg';
import moonUrl from '/img/moon.svg';

const isDark = ref(false);

const body = ref(null);

// Set the local ref and update local storage
const setDarkMode = (value) => {
  isDark.value = value;
  localStorage.setItem('theme', value ? 'dark' : '');
  body.value.classList.toggle('dark', value);
};

onMounted(() => {
  body.value = document.querySelector('html');
  // Check if the local storage is set or if user prefers dark
  const prefersDark =
    localStorage.getItem('theme') === 'dark' ||
    (!('theme' in localStorage) &&
      window.matchMedia('(prefers-color-scheme: dark)').matches);
  setDarkMode(prefersDark);
});

let imagePath = computed(() => {
  return isDark.value ? sunUrl : moonUrl;
});
</script>
<template>
  <!-- Wrapper -->
  <div
    class="select-none cursor-pointer w-14 overflow-hidden rounded-full p-1 bg-slate-800 dark:bg-slate-50"
    @click="setDarkMode(!isDark)"
  >
    <!-- Icon -->
    <div
      class="flex w-6 aspect-square rounded-full bg-yellow-500 transition-transform duration-200 ease"
      :class="isDark ? 'translate-x-0' : 'translate-x-full'"
    >
      <img :src="imagePath" />
    </div>
  </div>
</template>

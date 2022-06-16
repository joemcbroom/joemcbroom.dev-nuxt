<template>
  <div class="min-h-screen flex flex-col justify-start mx-auto">
    <Transition>
      <img :src="bgImage" class="-z-10 absolute top-0 left-0" v-if="bgImage" />
    </Transition>
    <NavigationBar />
    <main
      class="text-center z-10 bg-zinc-200 bg-opacity-25 rounded min-h-[400px] lg:mx-8 mt-4 p-4 overflow-hidden"
    >
      <h1 class="text-3xl">{{ route.meta.title }}</h1>
      <slot />
    </main>
  </div>
</template>

<script setup>
defineProps({
  bgImage: {
    type: String,
    default: null,
  },
});
const route = useRoute();
</script>

<style>
.v-enter-active,
.v-leave-active {
  transition: filter 0.2s ease;
}

.v-enter-from,
.v-leave-to {
  filter: blur(10px) grayscale(100%);
}
</style>

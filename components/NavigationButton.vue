<script setup>
defineProps({
  text: {
    type: String,
    default: '',
  },
  animated: {
    type: Boolean,
    default: false,
  },
  to: {
    type: String,
    default: '/',
  },
});
</script>

<template>
  <NuxtLink :to="to" class="inline-flex items-center justify-center group">
    <slot />
    <span
      class="pl-1 group-hover:scale-x-100 group-hover:text-teal-600 transition-transform transform origin-left"
      :class="animated ? 'scale-x-0' : 'scale-x-100'"
    >
      {{ text }}
    </span>
  </NuxtLink>
</template>

<template>
  <nav
    class="w-full sm:flex-nowrap sm:justify-end flex items-center flex-wrap justify-center gap-4 px-4 my-4 overflow-hidden transition-all duration-300 origin-top-right max-h[200px] z-20"
    :class="showNav ? 'max-h-[200px]' : 'max-h-0 sm:max-h-[200px]'"
  >
    <NavigationButton
      to="/"
      text="Joe McBroom"
      class="w-full sm:w-auto sm:mr-auto"
    >
      <img
        src="/img/profile.jpg"
        alt="Joe McBroom"
        class="w-12 aspect-1 rounded-full hover:w-20 hover:shadow hover:shadow-zinc-50 transition-all"
      />
    </NavigationButton>
    <NavigationButton to="/" text="Home">
      <HomeIcon class="w-5 text-teal-700 dark:text-teal-200" />
    </NavigationButton>
    <NavigationButton to="/resume" text="Resume">
      <DocumentTextIcon class="w-5 text-teal-700 dark:text-teal-200" />
    </NavigationButton>
    <NavigationButton to="/contact" text="Contact">
      <MailIcon class="w-5 text-teal-700 dark:text-teal-200" />
    </NavigationButton>
    <DarkSelector />
  </nav>
  <button
    @click="showNav = !showNav"
    class="sm:hidden absolute top-2 right-2 z-50"
  >
    <MenuIcon class="w-8 text-teal-700 dark:text-teal-200" />
  </button>
</template>
<script setup>
import {
  HomeIcon,
  QuestionMarkCircleIcon,
  MailIcon,
  MenuIcon,
  DocumentTextIcon,
} from '@heroicons/vue/solid';

const showNav = ref(false);
</script>

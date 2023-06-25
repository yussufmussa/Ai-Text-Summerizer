<template>
  <div>

<nav class="bg-teal-500 text-white dark:bg-gray-900 fixed w-full z-20 top-0 left-0 border-b border-gray-200 dark:border-gray-600">
  <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
    <h1 class="text-white text-2xl font-bold">Ai Text Shortner</h1>
  </div>
</nav>

    <TextShortener />
  </div>
</template>

<script>
import TextShortener from './components/TextShortener.vue';

export default {
  components: {
    TextShortener,
  },
};
</script>


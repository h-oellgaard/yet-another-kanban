<!-- filepath: /c:/Users/heoe/Projects/another-Kanban/layouts/default.vue -->
<template>
  <div>
    <Header />
    <NuxtLayout>
      <Nuxt />
    </NuxtLayout>
  </div>
</template>

<script>    
import { defineComponent } from 'vue';
import Header from '~/components/header.vue';

export default defineComponent({
  components: {
    Header
  }
});
</script>

<style>
/* Add any global styles if needed */
</style>
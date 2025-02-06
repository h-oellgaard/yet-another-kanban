<template>
  <section class="section">
    <div class="container">
      <h1 class="title">About Us</h1>
      <p class="content">
        Welcome to the Another Kanban application. This project is built using Nuxt.js, Vue 3, and Bulma. Our goal is to provide a simple and efficient way to manage your tasks using a Kanban board.
      </p>
    </div>
  </section>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'AboutPage'
});
</script>

<style scoped>
h1 {
  color: #333;
}
</style>

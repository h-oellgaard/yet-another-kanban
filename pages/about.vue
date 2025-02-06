<template>
  <section class="section">
    <div class="container">
      <h1 class="title">About Us</h1>
      <p class="content">
        Welcome to the Another Kanban application. This project is built using Nuxt.js, Vue 3, and Bulma. Our goal is to provide a simple and efficient way to manage your tasks using a Kanban board.
      </p>
      <h2 class="subtitle">Data Protection</h2>
      <p class="content">
        You can choose to have a personal board that saves data locally. However, you can only use one device. If you are in a team or want to access from multiple devices, you need to sign up. We will store your data securely in our servers.
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
.subtitle {
  margin-top: 20px;
  color: #555;
}
</style>

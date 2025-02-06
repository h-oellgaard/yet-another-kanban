<template>
  <section class="hero is-primary is-fullheight">
    <div class="hero-body">
      <div class="container has-text-centered">
        <h1 class="title">
          Welcome to Yet Another Kanban. 
        </h1>
        <h2 class="subtitle">
          Manage your personal, work and community commitments or any other task efficiently using only one Kanban board.
        </h2>
        <nuxt-link to="/board" class="button is-light is-large">
          Get Started
        </nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HomePage'
});
</script>

<style scoped>
.hero {
  background-image: url('https://source.unsplash.com/1600x900/?kanban,board');
  background-size: cover;
  background-position: center center;
}
</style>

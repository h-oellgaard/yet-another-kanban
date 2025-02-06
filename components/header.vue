<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <nuxt-link class="navbar-item" to="/">
        Home
      </nuxt-link>
      <nuxt-link class="navbar-item" to="/board">
        Board
      </nuxt-link>
    </div>
    <div class="navbar-end">
      <nuxt-link class="navbar-item is-small" to="/about">
        About
      </nuxt-link>
    </div>
  </nav>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Header'
});
</script>

<style scoped>
.navbar {
  background-color: #333;
  color: white;
}
.navbar-item {
  color: white;
}
.navbar-item:hover {
  background-color: #444;
}
.is-small {
  font-size: 0.875rem; /* Bulma's small font size */
}
</style>
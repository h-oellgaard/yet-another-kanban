<template>
  <section class="section">
    <div class="container">
      <h1 class="title">Kanban Board</h1>
      <p class="content">
        Manage your tasks efficiently using our Kanban board.
      </p>
      <!-- Add your board content here -->
    </div>
  </section>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'BoardPage'
});
</script>

<style scoped>
.title {
  margin-top: 20px;
}
</style>
<template>
  <section class="section">
    <div class="container">
      <Board />
    </div>
  </section>
</template>

<script>
import { defineComponent } from 'vue';
import Board from '~/components/board.vue';

export default defineComponent({
  name: 'BoardPage',
  components: {
    Board
  }
});
</script>

<style scoped>
.title {
  margin-top: 20px;
}

.section {
  padding: 2rem 1.5rem;
}
</style>
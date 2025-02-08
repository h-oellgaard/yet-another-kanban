<template>
  <section class="section">
    <div class="container">
      <h1 class="title">Eisenhower Matrix</h1>
      <div class="matrix">
        <div class="quadrant" v-for="quadrant in quadrants" :key="quadrant.id">
          <h2 class="quadrant-title">{{ quadrant.title }}</h2>
          <div class="task" v-for="task in getTasks(quadrant.id)" :key="task.id">
            {{ task.title }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'EisenhowerPage',
  data() {
    return {
      quadrants: [
        { id: 1, title: 'Urgent & Important' },
        { id: 2, title: 'Not Urgent & Important' },
        { id: 3, title: 'Urgent & Not Important' },
        { id: 4, title: 'Not Urgent & Not Important' }
      ],
      tasks: [
        { id: 1, title: 'Task 1', quadrantId: 1 },
        { id: 2, title: 'Task 2', quadrantId: 2 },
        { id: 3, title: 'Task 3', quadrantId: 3 },
        { id: 4, title: 'Task 4', quadrantId: 4 }
      ]
    };
  },
  methods: {
    getTasks(quadrantId) {
      return this.tasks.filter(task => task.quadrantId === quadrantId);
    }
  }
});
</script>

<style scoped>
.section {
  padding: 2rem 1.5rem;
}
.matrix {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: 0; /* Remove space between quadrants */
}
.quadrant {
  background-color: #f0f0f0;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
.quadrant-title {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #333;
}
.task {
  background-color: #ffffff;
  padding: 1rem;
  margin-bottom: 0.75rem;
  border-radius: 8px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}
</style>

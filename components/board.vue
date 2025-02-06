<template>
  <div class="board">
    <div class="swimlane" v-for="swimlane in swimlanes" :key="swimlane.id">
      <h2 class="swimlane-title">{{ swimlane.title }}</h2>
      <div class="columns">
        <div class="column" v-for="column in columns" :key="column.id">
          <h3 class="column-title">{{ column.title }}</h3>
          <div class="task" v-for="task in getTasks(swimlane.id, column.id)" :key="task.id">
            {{ task.title }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Board',
  data() {
    return {
      swimlanes: [
        { id: 1, title: 'Swimlane 1' },
        { id: 2, title: 'Swimlane 2' }
      ],
      columns: [
        { id: 1, title: 'To Do' },
        { id: 2, title: 'In Progress' },
        { id: 3, title: 'Done' }
      ],
      tasks: [
        { id: 1, title: 'Task 1', swimlaneId: 1, columnId: 1 },
        { id: 2, title: 'Task 2', swimlaneId: 1, columnId: 2 },
        { id: 3, title: 'Task 3', swimlaneId: 2, columnId: 1 },
        { id: 4, title: 'Task 4', swimlaneId: 2, columnId: 3 }
      ]
    };
  },
  methods: {
    getTasks(swimlaneId, columnId) {
      return this.tasks.filter(task => task.swimlaneId === swimlaneId && task.columnId === columnId);
    }
  }
});
</script>

<style scoped>
.board {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}
.swimlane {
  background-color: #e0e0e0;
  padding: 2rem; /* Increased padding */
  border-radius: 4px;
}
.swimlane-title {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}
.columns {
  display: flex;
  gap: 1rem;
}
.column {
  background-color: #f4f4f4;
  padding: 1rem;
  border-radius: 4px;
  width: 300px;
}
.column-title {
  font-size: 1.25rem;
  margin-bottom: 1rem;
}
.task {
  background-color: #fff;
  padding: 0.5rem;
  margin-bottom: 0.5rem;
  border-radius: 4px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}
</style>

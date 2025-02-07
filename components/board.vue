<template>
  <div class="board">
    <div class="swimlane" v-for="swimlane in swimlanes" :key="swimlane.id">
      <h2 class="swimlane-title" @click="toggleCollapse(swimlane.id)">
        {{ swimlane.title }}
        <span class="collapse-icon">{{ swimlane.collapsed ? '+' : '-' }}</span>
      </h2>
      <div class="columns" v-if="!swimlane.collapsed">
        <div 
          class="column" 
          :class="{ 'shared-column': column.shared }" 
          v-for="column in getColumns(swimlane)" 
          :key="column.id" 
          @drop="onDrop($event, swimlane.id, column.id)" 
          @dragover="onDragOver($event)"
        >
          <h3 class="column-title">{{ column.title }}</h3>
          <button class="remove-column" @click="removeColumn(swimlane.id, column.id)">Remove</button>
          <div class="task" v-for="task in getTasks(swimlane.id, column.id)" :key="task.id" draggable="true" @dragstart="onDragStart($event, task)">
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
        { id: 1, title: 'Swimlane 1', columnIds: [1, 2, 3], collapsed: false },
        { id: 2, title: 'Swimlane 2', columnIds: [1, 2, 3], collapsed: false }
      ],
      columns: [
        { id: 1, title: 'To Do', shared: false },
        { id: 2, title: 'In Progress', shared: true },
        { id: 3, title: 'Done', shared: false }
      ],
      tasks: [
        { id: 1, title: 'Task 1', swimlaneId: 1, columnId: 1 },
        { id: 2, title: 'Task 2', swimlaneId: 1, columnId: 2 },
        { id: 3, title: 'Task 3', swimlaneId: 2, columnId: 1 },
        { id: 4, title: 'Task 4', swimlaneId: 2, columnId: 3 }
      ],
      draggedTask: null
    };
  },
  methods: {
    getColumns(swimlane) {
      return this.columns.filter(column => column.shared || swimlane.columnIds.includes(column.id));
    },
    getTasks(swimlaneId, columnId) {
      return this.tasks.filter(task => task.swimlaneId === swimlaneId && task.columnId === columnId);
    },
    onDragStart(event, task) {
      this.draggedTask = task;
      event.dataTransfer.effectAllowed = 'move';
    },
    onDragOver(event) {
      event.preventDefault();
      event.dataTransfer.dropEffect = 'move';
    },
    onDrop(event, swimlaneId, columnId) {
      event.preventDefault();
      if (this.draggedTask) {
        this.draggedTask.swimlaneId = swimlaneId;
        this.draggedTask.columnId = columnId;
        this.draggedTask = null;
      }
    },
    removeColumn(swimlaneId, columnId) {
      const swimlane = this.swimlanes.find(s => s.id === swimlaneId);
      if (swimlane) {
        swimlane.columnIds = swimlane.columnIds.filter(id => id !== columnId);
      }
    },
    toggleCollapse(swimlaneId) {
      const swimlane = this.swimlanes.find(s => s.id === swimlaneId);
      if (swimlane) {
        swimlane.collapsed = !swimlane.collapsed;
      }
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
  background-color: #f0f0f0;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
.swimlane-title {
  font-size: 1.75rem;
  margin-bottom: 1.5rem;
  color: #333;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.collapse-icon {
  font-size: 1.5rem;
  margin-left: 1rem;
}
.columns {
  display: flex;
  gap: 1.5rem;
}
.column {
  background-color: #ffffff;
  padding: 1.5rem;
  border-radius: 8px;
  width: 300px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  position: relative;
}
.shared-column {
  background-color: #e0f7fa; /* Light cyan for shared columns */
}
.column-title {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #555;
}
.remove-column {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  color: #ff0000;
  cursor: pointer;
}
.task {
  background-color: #fafafa;
  padding: 1rem;
  margin-bottom: 0.75rem;
  border-radius: 8px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  cursor: grab;
  transition: background-color 0.2s;
}
.task:active {
  cursor: grabbing;
}
.task:hover {
  background-color: #f0f0f0;
}
</style>

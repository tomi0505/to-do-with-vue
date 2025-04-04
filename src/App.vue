<template>
  <div class="container mt-5">
    <form>
      <div class="mb-3">
        <input type="email" class="form-control" placeholder="Zadanie do wykonania" v-model="taskName">
        <div class="form-text" v-show="taskNameIsEmpty">To pole nie może być puste!</div>
      </div>
      <button type="button" class="btn btn-primary" @click="addTask">Dodaj</button>

      <ul class="list-group">
        <TaskItem v-for="task in tasks" :key="task.id" :id="task.id" :name="task.name" :removeTask="removeTask"/>
      </ul>
    </form>
  </div>
</template>

<script>
import TaskItem from './components/TaskItem.vue';

export default {
  name: 'App',
  components: {
    TaskItem
  },
  data() {
    return {
      taskName: '',
      tasks: [],
      taskNameIsEmpty: false
    }
  },
  methods: {
    addTask() {
      if (this.taskName.trim() !== '') {
        // NEW TASK PATTERN
        const task = {
          id: crypto.randomUUID(),
          name: this.taskName.trim()
        }
        // NEW TASK PATTERN END

        this.tasks.push(task);
        this.taskName = '';
        this.taskNameIsEmpty = false;
      } else {
        this.taskNameIsEmpty = true;
      }
    },
    removeTask(id) {
      const updatedTasks = this.tasks.filter(task => task.id !== id);
      this.tasks = updatedTasks;
    }
  }
}
</script>

<style>
body {
  background-color: #5f9ea0;
}
</style>
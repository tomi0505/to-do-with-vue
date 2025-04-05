<template>
  <div class="container mt-5">
    <form @submit.prevent class="d-md-flex">
      <input type="text" class="form-control" placeholder="Zadanie do wykonania" v-model="taskName"
        @keyup.enter="addTask">
      <div class="form-text d-md-none" v-show="taskNameIsEmpty">To pole nie może być puste!</div>
      <button type="button" class="btn btn-primary d-block mt-2 mt-md-0 ms-md-2 add-task-btn-b"
        @click="addTask">Dodaj</button>
    </form>
    <div class="form-text d-none d-md-block" :class="taskNameIsEmpty ? 'd-block' : 'd-md-none-b'">To pole nie może być
      puste!</div>
    <ul class="list-group mt-4">
      <TaskItem v-for="task in tasks.filter(task => task.done === false)" :key="task.id" :id="task.id" :name="task.name" :done="task.done" :removeTask="removeTask" :changeTaskIsDone="changeTaskIsDone" />
    </ul>
  </div>
</template>

<script>
import DoneTasks from './DoneTasks.vue';
import TaskItem from './TaskItem.vue';

export default {
  components: {
    DoneTasks,
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
          name: this.taskName.trim(),
          done: false
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
    },
    changeTaskIsDone(id, done) {
      if(done) {
        const tasks = [...this.tasks];
        const updatedTask = tasks.find(task => task.id === id);
        if(updatedTask) {
          updatedTask.done = true;
        }
        this.tasks = tasks;
      } else {
        const tasks = [...this.tasks];
        const updatedTask = tasks.find(task => task.id === id);
        if(updatedTask) {
          updatedTask.done = false;
        }
        this.tasks = tasks;
      }
    }
  }
}
</script>

<style scoped>
.d-md-none-b {
  @media (min-width: 768px) {
    display: none !important;
  }
}

.add-task-btn-b {
  @media(max-width: 767px) {
    width: 100%;
  }
}
</style>
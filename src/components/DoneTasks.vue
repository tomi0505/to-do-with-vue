<template>
  <div class="container mt-5">
    <ul class="list-group mt-4">
      <TaskItem v-for="task in tasks.filter(task => task.done === true)" :key="task.id" :id="task.id" :name="task.name"
        :done="task.done" :removeTask="removeTask" :changeTaskIsDone="changeTaskIsDone" />
    </ul>
  </div>
</template>

<script>
import TaskItem from './TaskItem.vue';

export default {
  components: {
    TaskItem
  },
  props: {
    tasks: Array,
    removeTask: Function,
    changeTaskIsDone: Function
  }
}
</script>
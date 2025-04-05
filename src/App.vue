<template>
  <header>

  </header>
  <main>
    <ToDoList/>
  </main>
</template>

<script>
import ToDoList from './components/ToDoList.vue';

export default {
  name: 'App',
  components: {
    ToDoList
  }
}
</script>
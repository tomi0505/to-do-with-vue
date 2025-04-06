<template>
  <li class="list-group-item d-flex align-items-center">
    <span class="ms-1">{{ name }}</span>
    <button type="button" class="btn btn-secondary ms-auto" @click="restoreTask(id)">Przywróć</button>
    <button type="button" class="btn btn-secondary ms-2" @click="removeTask(id)">Usuń na zawsze</button>
  </li>
</template>

<script>
export default {
  name: 'TaskItem',
  props: {
    id: String,
    name: String,
    removeTask: Function,
    restoreTask: Function
  }
}
</script>
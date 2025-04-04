<template>
  <li class="list-group-item d-flex align-items-center">
    <input class="form-check-input me-1" type="checkbox" value="" :id="id">
    <label class="form-check-label d-flex align-items-center w-100" :for="id">
      <span class="ms-1">{{ name }}</span>
      <button type="button" class="btn btn-secondary ms-auto" @click="removeTask(id)">Usuń</button>
    </label>
  </li>
</template>

<script>
export default {
  name: 'TaskItem',
  props: {
    name: String,
    id: String,
    removeTask: Function
  }
}
</script>
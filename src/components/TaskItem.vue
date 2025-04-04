<template>
  <li class="list-group-item">
    <input class="form-check-input me-1" type="checkbox" value="" :id="id">
    <label class="form-check-label" :for="id">{{ name }}</label>
  </li>
</template>

<script>
export default {
  name: 'TaskItem',
  props: {
    name: String,
    id: String
  }
}
</script>
<template>
  <li>
    {{ todo.category }}: {{ todo.name }} due on {{ todo.dueDate }}
    <button>Add reminder</button>
    <button @click="$emit('remove', todo.id)">X</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
  button {
    padding: 2px 3px;
    margin-left: 4px;
  }
</style>

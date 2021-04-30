<template>
  <li>
    {{ todo.category }}: {{ todo.name }} due {{ todo.dueDate }}
    <!-- <v-btn color="secondary" small >Add reminder</v-btn> -->
    <v-btn color="secondary" small @click="$emit('remove', todo.id)">X</v-btn>
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

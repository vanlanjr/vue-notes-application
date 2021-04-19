<template>
  <li>
    {{ todo.text }}
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

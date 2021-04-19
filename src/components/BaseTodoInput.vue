<template>
  <div>
    <BaseInputText
      placeholder="Todo category"
    />
    <BaseInputText
      placeholder="Todo name"
    />
    <BaseInputText
      placeholder="Todo due date"
    />
    <button @click="addTodo" :disabled="addDisabled">Add Todo Item</button>
  </div>
</template>

<script>
import BaseInputText from './BaseInputText.vue'

export default {
  name: 'BaseTodoInput',
  components: {
    BaseInputText
  }
}
</script>

<style scoped>
  button {
    width: 105%;
    padding: 8px 10px;
  }
</style>

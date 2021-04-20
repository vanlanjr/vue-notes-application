<template>
  <div>
    <BaseTodoInput />
    <button @click="$emit('add')">Add Todo Item</button>
    <ul v-if="todos.length">
      <TodoListItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @remove="removeTodo"
      />
    </ul>
    <p v-else>Nothing left in the list. Add a new todo in the input above.</p>
  </div>
</template>

<script>
import BaseTodoInput from './BaseTodoInput.vue'
import TodoListItem from './TodoListItem.vue'

let nextTodoId = 1

export default {
  components: {
    BaseTodoInput,
    TodoListItem
  },
  data () {
    return {
      newTodoCategory: '',
      newTodoName: '',
      newTodoDueDate: '',
      todos: [
        {
          id: nextTodoId++,
          category: 'ISAT 252',
          name: 'Learn Vue',
          dueDate: 'March 4th'

        },
        {
          id: nextTodoId++,
          category: 'ISAT 252',
          name: 'Complete Project',
          dueDate: 'March 6th'
        }
      ]
    }
  },
  methods: {
    addTodo () {
      const trimmedCategory = this.newTodoCategory.trim()
      const trimmedName = this.newTodoName.trim()
      const trimmedDueDate = this.newTodoDueDate.trim()
      if (trimmedName) {
        this.todos.push({
          id: nextTodoId++,
          category: trimmedCategory,
          name: trimmedName,
          dueDate: trimmedDueDate
        })
        this.newTodoCategory = ''
        this.newTodoName = ''
        this.newTodoDueDate = ''
      }
    },
    removeTodo (idToRemove) {
      this.todos = this.todos.filter((todo) => {
        return todo.id !== idToRemove
      })
    }
  }
}
</script>

<style scoped>
  li {
    margin-bottom: 4px;
  }
</style>

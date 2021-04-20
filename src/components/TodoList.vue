<template>
  <div>
    <!-- <BaseTodoInput
      @add="addTodo"/> -->
    <!-- <button @click="addTodo">Add Todo Item</button> -->
    <BaseInputText
      v-model="newTodoCategory"
      placeholder="Todo category"
    />
    <BaseInputText
      v-model="newTodoName"
      placeholder="Todo name"
    />
    <BaseInputText
      v-model="newTodoDueDate"
      placeholder="Todo due date"
    />
    <button @click="addTodo">Add Todo Item</button>
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
// import BaseTodoInput from './BaseTodoInput.vue'
import TodoListItem from './TodoListItem.vue'
import BaseInputText from './BaseInputText.vue'

// const DB_NAME = 'tododb'
// const DB_VERSION = 1

let nextTodoId = 1

export default {
  components: {
    BaseInputText,
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
      // // database data
      // db: this.getDb(),
      // ready: false,
      // addDisabled: false,
      // async created () {
      //   this.db = await this.getDb()
      //   this.todos = await this.getTodosFromDb()
      //   this.ready = true
      // }
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
    // async addTodo () {
    //   this.addDisabled = true
    //   // random todo for now
    //   const todo = {
    //     newTodoCategory: this.newTodoCategory.trim(),
    //     newTodoName: this.newTodoName.trim(),
    //     newTodoDueDate: this.newTodoDueDate.trim()
    //   }
    //   await this.addTodoToDb(todo)
    //   this.todos = await this.getTodosFromDb()
    //   this.addDisabled = false
    // },
    removeTodo (idToRemove) {
      this.todos = this.todos.filter((todo) => {
        return todo.id !== idToRemove
      })
    }
    // async removeTodo (id) {
    //   await this.deleteTodoFromDb(id)
    //   this.todos = await this.getTodosFromDb()
    // },
    // async addTodoToDb (todo) {
    //   return new Promise((resolve, reject) => {
    //     const trans = this.db.transaction(['todos'], 'readwrite')
    //     trans.oncomplete = e => {
    //       resolve()
    //     }
    //     const store = trans.objectStore('todos')
    //     store.add(todo)
    //   })
    // },
    // async deleteTodoFromDb (id) {
    //   return new Promise((resolve, reject) => {
    //     const trans = this.db.transaction(['todos'], 'readwrite')
    //     trans.oncomplete = e => {
    //       resolve()
    //     }

    //     const store = trans.objectStore('todos')
    //     store.delete(id)
    //   })
    // },
    // async getTodosFromDb () {
    //   return new Promise((resolve, reject) => {
    //     const trans = this.db.transaction(['todos'], 'readonly')
    //     trans.oncomplete = e => {
    //       resolve(todos)
    //     }
    //     const store = trans.objectStore('todos')
    //     const todos = []
    //     store.openCursor().onsuccess = e => {
    //       const cursor = e.target.result
    //       if (cursor) {
    //         todos.push(cursor.value)
    //         cursor.continue()
    //       }
    //     }
    //   })
    // },
    // async getDb () {
    //   return new Promise((resolve, reject) => {
    //     const request = window.indexedDB.open(DB_NAME, DB_VERSION)
    //     request.onerror = e => {
    //       console.log('Error opening db', e)
    //       reject(e)
    //     }
    //     request.onsuccess = e => {
    //       resolve(e.target.result)
    //     }
    //     request.onupgradeneeded = e => {
    //       console.log('onupgradeneeded')
    //       // const db = e.target.result
    //       // const objectStore = db.createObjectStore("todos", { autoIncrement: true, keyPath:'id'})
    //     }
    //   })
    // }
  }
}
</script>

<style scoped>
  li {
    margin-bottom: 4px;
  }
</style>

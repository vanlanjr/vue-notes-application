<template>
  <div>
    <!-- Notes Nav Bar-->
    <div id="left-note-nav-bar">
      <ul v-if="notes.length">
        <TodoList
          v-for="note in notes"
          :key="note.id"
          :note="note"
        />
      </ul>
      <p v-else>Add a New Note</p>
    </div>
    <!-- Current Note View -->
    <div id="current-note-view">
      <TodoList

      />
    </div>
  </div>
</template>

<script>

</script>

<style>

</style>

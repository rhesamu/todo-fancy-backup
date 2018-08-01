<template>
  <div>
    <Todo v-for="(todo, index) in todos"
      :key="index"
      :todo="todo"
      @complete-todo="completeTodo"
      @uncomplete-todo="uncompleteTodo"
      @delete-todo="deleteTodo" />
  </div>
</template>

<script>
import Todo from "@/components/Todo.vue"

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    completeTodo (todo) {
      const index = this.todos.indexOf(todo)
      this.todos[index].done = true
    },
    uncompleteTodo (todo) {
      const index = this.todos.indexOf(todo)
      this.todos[index].done = false
    },
    deleteTodo (todo) {
      const index = this.todos.indexOf(todo)
      this.todos.splice(index, 1)
    }
  }
}
</script>

<style>

</style>



<template>
  <div>
    <Todo v-for="(todo, index) in todos"
      :key="index"
      :todo="todo"
      @complete-todo="completeTodo"
      @uncomplete-todo="uncompleteTodo"
      @edit-todo="editTodo"
      @delete-todo="deleteTodo" />
  </div>
</template>

<script>
import axios from 'axios'
import Todo from "@/components/Todo.vue"

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    completeTodo (todo) {
      let token = localStorage.getItem('token')
      console.log(todo)
      
      axios.put(`http://todo-api.rhesautomo.com/api/${todo._id}`, {
        done: true
      })
      .then(response => {
        console.log('success',response)
        const index = this.todos.indexOf(todo)
        this.todos[index].done = true
      })
      .catch(err => {
        console.log('error', err)
      })
    },
    uncompleteTodo (todo) {
      let token = localStorage.getItem('token')
      console.log(todo)
      
      axios.put(`http://todo-api.rhesautomo.com/api/${todo._id}`, {
        done: false
      })
      .then(response => {
        console.log('success',response)
        const index = this.todos.indexOf(todo)
        this.todos[index].done = false
      })
      .catch(err => {
        console.log('error', err)
      })
    },
    editTodo (todo) {
      let token = localStorage.getItem('token')
      console.log(todo)
      axios.put(`http://todo-api.rhesautomo.com/api/${todo._id}`, todo)
      .then(response => {
        console.log('success', response)
      })
      .catch(err => {
        console.log('error', err)
      })
    },
    deleteTodo (todo) {
      let token = localStorage.getItem('token')
      console.log(todo)

      axios.delete(`http://todo-api.rhesautomo.com/api/${todo._id}`)
      .then(response => {
        console.log('deleted', response)
        const index = this.todos.indexOf(todo)
        this.todos.splice(index, 1)
      })
      .catch(err => {
        console.log('error', err)
      })
      
    }
  }
}
</script>

<style>

</style>



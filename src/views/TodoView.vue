<template>
  <div id="todoview">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <TodoList
      :todos="todos" />
    <CreateTodo
      @create-todo="createTodo" />
  </div>
</template>

<script>
import axios from 'axios'
import TodoList from '@/components/TodoList.vue'
import CreateTodo from '@/components/CreateTodo.vue'

export default {
  name: 'todoview',
  components: {
    TodoList,
    CreateTodo
  },
  data () {
    return {
      todos: []
    }
  },
  mounted () {
    let token = localStorage.getItem('token')
    console.log(token)
    if (!token) {
      this.$router.push('/login')
    }

    axios.get('http://todo-api.rhesautomo.com/api/todos', {
      headers: { token }
    })
    .then(response => {
      console.log(response)
      this.todos = response.data.todos
    })
    .catch(err => {
      console.log('error', err)
    })
  },
  methods: {
    createTodo (newTodo) {
      let token = localStorage.getItem('token')
      axios.post('http://todo-api.rhesautomo.com/api/todos', newTodo, {
        headers: { token }
      })
      .then(response => {
        console.log('success', response)
      })
      .catch(err => {
        console.log('error', err)
      })
      console.log(newTodo)
      this.todos.push(newTodo)
    }
  }
}
</script>

 
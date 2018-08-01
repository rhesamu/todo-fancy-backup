<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <TodoList
      :todos="todos" />
    <CreateTodo
      @create-todo="createTodo" />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TodoList from './components/TodoList.vue'
import CreateTodo from './components/CreateTodo.vue'

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo
  },
  data () {
    return {
      todos: [
        {
          title: 'Todo A',
          deadline: 'deadline A',
          done: false
        }, {
          title: 'Todo B',
          deadline: 'deadline B',
          done: true
        }, {
          title: 'Todo C',
          deadline: 'deadline C',
          done: false
        }, {
          title: 'Todo D',
          deadline: 'deadline D',
          done: false
        }
      ]
    }
  },
  methods: {
    createTodo (newTodo) {
      console.log(newTodo)
      this.todos.push(newTodo)
    }
  }
}
</script>

<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i> Add new task
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="title" type='text' defaultValue="">
          </div>
          <div class='field'>
            <label>Deadline</label>
            <input type='date' v-model='deadline'>
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">
              Create
            </button>
            <button class='ui basic red button' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: '',
      deadline: null,
      isCreating: false
    }
  },
  methods: {
    openForm () {
      this.isCreating = true
    },
    closeForm () {
      this.isCreating = false
    },
    sendForm () {
      if (this.title.length > 0 && this.deadline) {
        const title = this.title
        const deadline = this.deadline
        const newTodo = {
          title, deadline, done: false
        }
        this.title = ''
        this.deadline = null

        this.$emit('create-todo', newTodo)
      }
      this.isCreating = false
    }
  }
}
</script>

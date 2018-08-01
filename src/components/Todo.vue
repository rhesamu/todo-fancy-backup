<template>
  <div class="ui centered card">
    <div class="content" v-show="!isEditing">
      <div class="header">
        {{ todo.title }}
      </div>
      <div class="meta">
        {{ todo.deadline }}
      </div>
      <div class="extra content">
        <span class="right floated edit icon" v-on:click="showForm">
          <i class="edit icon"></i>
        </span>
        <span class="right floated trash icon" v-on:click="deleteTodo(todo)">
          <i class="trash icon"></i>
        </span>
      </div>
    </div>

    <div class="content" v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label>Title</label>
          <input type="text" name="title" v-model="todo.title">
        </div>
        <div class="field">
          <label>Deadline</label>
          <input type="date" name="deadline" v-model="todo.deadline">
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic blue button" v-on:click="hideForm">
            Edit
          </button>
        </div>
      </div>
    </div>

    <div class="ui bottom attached green basic button" v-show="!isEditing && todo.done" v-on:click="uncompleteTodo(todo)">
      Completed
    </div>
    <div class="ui bottom attached red basic button" v-show="!isEditing && !todo.done" v-on:click="completeTodo(todo)">
      Pending
    </div>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  data () {
    return {
      isEditing: false
    }
  },
  methods: {
    completeTodo (todo) {
      this.$emit('complete-todo', todo)
    },
    uncompleteTodo (todo) {
      this.$emit('uncomplete-todo', todo)
    },
    deleteTodo (todo) {
      console.log(todo)
      this.$emit('delete-todo', todo)
    },
    showForm () {
      this.isEditing = true
    },
    hideForm () {
      this.isEditing = false
    }
  }
}
</script>

<style>

</style>

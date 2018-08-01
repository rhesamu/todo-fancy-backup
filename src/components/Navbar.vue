<template>
  <div class="ui secondary menu">
    <div class="right menu">
      <div class="item">
        <button class="ui button" v-on:click="logout">Logout</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$emit('logout', {})
    }
  }
}
</script>


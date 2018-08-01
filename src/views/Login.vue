<template>
  <div class="ui middle aligned center aligned grid" id="loginbox">
    <div class="column">
      <h2 class="ui image header">
        <div class="content">
          Todo Fancy
        </div>
      </h2>
      <form @submit.prevent="login" class="ui large form">
        <div class="ui stacked secondary segment">
          <div class="field">
            <label>Email</label>
            <input type="text" name="email" placeholder="Email address" v-model="email">
          </div>
          <div class="field">
            <label>Password</label>
            <input type="password" name="password" placeholder="Password" v-model="password">
          </div>
          <button class="ui button teal" type="submit">Login</button>
        </div>
      </form>
      <div class="ui message">
        Don't have an account? <router-link to="/register">Register</router-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    login () {
      let self = this
      axios.post('http://todo-api.rhesautomo.com/api/login', {
        email: this.email,
        password: this.password
      })
      .then(response => {
        if (response.data.token) {
          console.log('success -->', response)
          localStorage.setItem('token', response.data.token)
          this.$router.push('/')
        }
      })
      .catch(err => {
        console.log('err -->',err)
      })
    }
  }
}
</script>


<style scoped>
  #loginbox {
    margin-top: 80px;
  }
  .column {
    max-width: 400px;
  }
</style>

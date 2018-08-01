<template>
  <div class="ui middle aligned center aligned grid" id="register">
    <div class="column">
      <h2 class="ui image header">
        <div class="content">
          Register
        </div>
      </h2>
      <form @submit.prevent="register" class="ui large form">
        <div class="ui stacked secondary segment">
          <div class="field">
            <label>Email</label>
            <input type="text" name="email" placeholder="Email" v-model="email">
          </div>
          <div class="field">
            <label>Password</label>
            <input type="password" name="password" placeholder="Password" v-model="password">
          </div>
          
          <button class="ui button teal" type="submit">Register</button>
        </div>
      </form>

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
    register () {
      axios.post('http://todo-api.rhesautomo.com/api/register', {
        email: this.email,
        password: this.password
      })
      .then(response => {
        console.log('success',response)
        this.$router.push('/login')
      })
      .catch(err => {
        console.log('error', err)
      })
    }
  }
}
</script>


<style scoped>
  #register {
    margin-top: 80px;
  }
  .column {
    max-width: 400px;
  }
</style>

<template>
  <div id="app">
    <Navbar 
      v-show="isLoggedIn"
      @logout="logout"/>
    <router-view/>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'

export default {
  data () {
    return {
      isLoggedIn: false
    }
  },
  components: {
    Navbar
  },
  created () {
    let token = localStorage.getItem('token')
    if (token) {
      this.isLoggedIn = true
    } else {
      this.$router.push('/login')
    }
  },
  methods: {
    logout() {
      this.isLoggedIn = false
      localStorage.removeItem('token')
      this.$router.push('/login')
    }
  }
}
</script>


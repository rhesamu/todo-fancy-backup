<template>
  <div id="app">
    <Navbar v-show="isLoggedIn"/>
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
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
  }
}
</script>


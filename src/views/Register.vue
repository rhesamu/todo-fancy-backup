<template>
  <div class="ui middle aligned center aligned grid" id="register">
    <div class="column">
      <h2 class="ui image header">
        <div class="content">
          Register
        </div>
      </h2>
      <form class="ui large form">
        <div class="ui stacked secondary segment">
          <div class="field">
            <label>Email</label>
            <input type="text" name="first-name" placeholder="First Name">
          </div>
          <div class="field">
            <label>Password</label>
            <input type="text" name="last-name" placeholder="Last Name">
          </div>
          
          <button class="ui button teal" type="submit">Register</button>
        </div>
      </form>

    </div>
  </div>
</template>


<style scoped>
  #register {
    margin-top: 80px;
  }
  .column {
    max-width: 400px;
  }
</style>

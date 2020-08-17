<template>
  <div id="nav">
    <div>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
    <div class="right-nav">
      <!-- <router-link to="/world/1">World</router-link> -->
      <router-link to="/login">Login</router-link>
      <router-link to="/signup">Signup</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Nav'
}
</script>

<style lang="scss" scoped>
#nav {
  width: 100%;
  display: flex;
  flex-direction: row;
  background-color: #2c3e50;
  justify-content: space-between;
  div {
    display: flex;
    flex-direction: row;
    a {
      font-weight: bold;
      color: #2c3e50;
      display: block;
      width: 85px;
      padding: 15px;
      background-color: #42b983;
      text-decoration: none;
      box-sizing: border-box;
      &.router-link-exact-active {
        //background-color: #fab;
      }
    }
    a:hover {
      background-color: #2c3e50;
      color: #42b983;
    }
  }
}
</style>

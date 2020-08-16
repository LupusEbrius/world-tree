<template>
  <div class="signup">
    <form action="signup" method="post" class="login-form">
        <h2>Sign Up</h2>
        <label for="email">Email</label>
      <input type="text" placeholder="Email" />
      <label for="username">Username</label>
      <input type="text" placeholder="Username" />
      <label for="password">Password</label>
      <input type="password" placeholder="Password" />
      <label for="confirm-password"> Confirm Password</label>
      <input type="password" placeholder="Confirm Password" />
      <input type="submit" id="submit" value="Sign Up" />
      <router-link to="/login" class="link switch">Already have an account? Login here</router-link>
    </form>
  </div>
</template>
<script>
import { Auth } from 'aws-amplify';
export default {
  data: function(){
    return {
      username,
      email,
      password,
      error
    }
  },
  methods:{
    Signup: () => {
      const{ username, email, password } = this.data;
      try{
        const signupRes = await Auth.signUp({
          username,
          password,
          attribute:{
            email: email
          }
        });
      }catch(err){
        this.data.error = err;
      }
    }
  }
}
</script>

<style lang="scss">
// .signup {
//   background-color: #ddd;
//   height: 100%;
//   width: 100%;
//   position: fixed;
// }
// form {
//   width: 20%;
//   display: flex;
//   height: max-content;
//   flex-direction: column;
//   background-color: #fff;
//   height: 60%;
//   margin: auto;
//   margin-top: 8%;
//   box-sizing: border-box;
// }
</style>

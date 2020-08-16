<template>
    <div class="login">
        <form action="login" method="POST" class="login-form">
            <h2>Login</h2>
            <label for="username">Username</label>
            <input type="text" placeholder="Username or Email" />
            <label for="password">Password</label>
            <input type="password" placeholder="Password" />
            <input type="submit" id="submit" value="Login" />
            <router-link to="/forgot" class="link">Forgot Password</router-link>
            <router-link to="/signup" class="link switch">Don't have an account? Sign up here</router-link>
        </form>
    </div>
</template>

<style lang="scss">
.login, .signup {
    background-color: #ddd;
    height: 100%;
    width: 100%;
    position: fixed;
}
.login-form {
    width: 20%;
    display: flex;
    flex-direction: column;
    background-color: #fff;

    margin: auto;
    margin-top: 8%;
    box-sizing: border-box;
    label {
        margin: 0px auto;
        width: 70%;
        text-align: left;
    }
    input {
        width: 70%;
        margin: 10px auto;
        padding: 5px;
        box-sizing: border-box;
    }
    #submit {
        background-color: rgb(86, 86, 191);
        color: #fff;
        font-weight: 500;
        font-family: sans-serif;
        border: none;
        cursor: pointer;
    }
    .link {
        font-size: 12px;
    }
    .link:visited {
        color: #00f;
    }
    .switch {
        position: relative;
        bottom: 2%;
        width: 90%;
        text-align: center;
        margin: auto;
        padding: 25px 10px;
    }
}

@media screen and (max-width: 1000px) {
  .login-form {
    width: 80%;
  }
}

</style>

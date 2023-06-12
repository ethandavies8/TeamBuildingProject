<template>
  <div class="Form-Page">
    <div class="header">
      <div class="diamond"></div>
      <h1 class="center">{{ msg }}</h1>
      <div class="account-container">
        <label class="create-acccount-message"
          >Create an account to save player data</label
        ><br />
        <div class="register-login-box">
          <div class="register-box">
            <button
              for="register-dropdown-visible"
              class="register-button"
              v-on:click="setOpenDialog('register')"
            >
              <u>Register</u>
            </button>
            <input
              type="checkbox"
              id="register-dropdown-visible"
              class="register-dropdown-checkbox"
              v-model="isRegisterOpen"
            />
            <div class="register-dropdown-box-container">
              <div class="register-dropdown">
                <div class="register-header">
                  <h1>Register</h1>
                </div>
                <form class="sign-up-form" ref="registerForm">
                  <div class="email-info">
                    <input
                      type="text"
                      id="email"
                      name="username"
                      placeholder="Email"
                      class="email-input"
                      required
                      v-model="email"
                    />
                  </div>
                  <div class="username-info">
                    <input
                      type="text"
                      id="username"
                      name="password"
                      placeholder="Username"
                      class="register-username"
                      required
                      v-model="username"
                    />
                  </div>
                  <div class="password-info">
                    <input
                      type="password"
                      id="password"
                      placeholder="Password"
                      class="register-password"
                      required
                      v-model="password"
                    />
                  </div>
                  <div class="register-submit-button-box">
                    <input
                      type="submit"
                      value="Submit"
                      class="register-submit"
                      v-on:click="attemptRegister"
                    />
                  </div>
                </form>
              </div>
            </div>
          </div>
          <div class="login">
            <button v-on:click="setOpenDialog('signIn')" class="sign-in-button">
              <u>Sign in</u>
            </button>
            <input
              type="checkbox"
              id="sign-in-dropdown-visible"
              class="sign-in-dropdown-checkbox"
              v-model="isSignInOpen"
            />
            <div class="sign-in-dropdown-box-container">
              <div class="sign-in-dropdown">
                <div class="sign-in-header">
                  <h1>Sign In</h1>
                </div>
                <form class="sign-in-form" ref="loginForm">
                  <label class="needs-input"></label>
                  <div class="username-info">
                    <input
                      type="text"
                      placeholder="Username"
                      class="login-username"
                      id="username"
                      required
                      v-model="username"
                    />
                  </div>
                  <div class="password-info">
                    <input
                      type="password"
                      placeholder="Password"
                      class="login-password"
                      id="password"
                      required
                      v-model="password"
                    />
                  </div>
                  <div class="login-submit-button-box">
                    <input
                      type="submit"
                      value="Submit"
                      class="login-submit"
                      v-on:click="attemptLogin"
                    />
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { Options, Vue } from "vue-class-component";
@Options({
  props: {
    msg: String,
  },
})
export default class Header extends Vue {
  msg!: string;
  openDialog?: string | null;
  isSignInOpen = false;
  isRegisterOpen = false;
  username?: string | null;
  password?: string | null;
  email?: string | null;

  public setOpenDialog(name?: string): void {
    if (this.openDialog === name) {
      this.openDialog = null;
    } else {
      this.openDialog = name;
    }
    this.isSignInOpen = this.openDialog === "signIn";
    this.isRegisterOpen = this.openDialog === "register";
    //default user input values back to null
    this.username = null;
    this.password = null;
    this.email = null;
  }

  public attemptRegister(): void {
    if (this.username === null || this.password === null || this.email === null)
      return;
    //alert to be replaced with API Call
    alert(
      "Attempt to register user with Email: " +
        this.email +
        " Username: " +
        this.username +
        " Password: " +
        this.password
    );
  }

  public attemptLogin(): void {
    if (this.username === null || this.password === null) return;
    //alert to be replaced with API call
    alert(
      "Attempt to login user with Username: " +
        this.username +
        " Password: " +
        this.password
    );
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@use "../assets/style.scss";
.register-button {
  background-color: #ffffff;
  width: 72px;
  height: 32px;
  text-align: center;
  color: black;
  vertical-align: middle;
  border: 1 px solid black;
}

.sign-in-button {
  background-color: #03a9f4;
  width: 72px;
  height: 32px;
  text-align: center;
  color: #ffffff;
  vertical-align: middle;
  border: 1px solid black;
}
.sign-in-form {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.sign-up-form {
  display: flex;
  align-items: center;
  flex-direction: column;
}
.sign-up-form input {
  outline: 0;
  background: #f2f2f2;
  width: 100%;
  border: 0;
  margin: 8px 0px 8px 0px;
  padding: 8px;
  box-sizing: border-box;
  font-size: 14px;
}
.sign-in-form input {
  outline: 0;
  background: #f2f2f2;
  width: 100%;
  border: 0;
  margin: 8px 0px 8px 0px;
  padding: 8px;
  box-sizing: border-box;
  font-size: 14px;
}
.sign-in-dropdown-checkbox {
  display: none;
}

.register-dropdown-checkbox {
  display: none;
}

.sign-in-dropdown-box-container {
  position: relative;
}

.register-dropdown-box-container {
  position: relative;
}

.sign-in-dropdown {
  position: absolute;
  height: 300px;
  width: 450px;
  transform: scale(0%);
  transition: transform 200ms ease-out;
  transform-origin: top right;
  background-color: white;
  border: 1px solid black;
}

.sign-in-dropdown h1 {
  color: black;
}

.sign-in-dropdown label {
  color: black;
}

.register-dropdown h1 {
  color: black;
}

.register-dropdown label {
  color: black;
}
.register-dropdown {
  position: absolute;
  height: 300px;
  width: 450px;
  transform: scale(0%);
  transition: transform 200ms ease-out;
  transform-origin: top right;
  background-color: white;
  border: 1px solid black;
  align-items: center;
}

.register-login-box {
  flex-direction: row;
}

.login {
  border: none;
  float: right;
  margin: 8px 8px 8px 24px;
  background-color: #03a9f4;
  width: 72px;
  height: 32px;
  text-align: center;
}
.register-box {
  float: right;
  margin: 8px 0px 8px 8px;
  background-color: #ffffff;
  width: 72px;
  height: 32px;
  text-align: center;
}
.register-button:hover {
  cursor: pointer;
  color: #03a9f4;
}

.sign-in-button:hover {
  cursor: pointer;
  color: black;
}

.login-submit:hover {
  cursor: pointer;
  background-color: #03a9f4;
}

.register-submit:hover {
  cursor: pointer;
  background-color: #03a9f4;
}

input.sign-in-dropdown-checkbox:checked
  ~ .sign-in-dropdown-box-container
  .sign-in-dropdown {
  transition: transform 200ms ease-in;
  transform: scale(100%);
  transform: translate(-290px, 11px);
}

input.register-dropdown-checkbox:checked
  ~ .register-dropdown-box-container
  .register-dropdown {
  transition: transform 200ms ease-in;
  transform: scale(100%);
  transform: translate(-379px, 11px);
}

.header {
  flex-direction: row;
  display: flex;
  height: 80px;
  width: 100%;
  background-color: #f44336;
  margin: 0;
  padding: 0;
  position: fixed;
  top: 0;
  left: 0;
}

.diamond {
  background: #fff;
  height: 32px;
  text-align: center;
  transform: rotate(45deg);
  width: 32px;
  margin-top: 24px;
  margin-bottom: 24px;
  margin-left: 32px;
  margin-right: 8px;
}

.center {
  float: center;
  text-align: left;
  margin-left: 8px;
  margin-bottom: 28px;
  margin-top: 28px;
  height: 24px;
  color: #ffffff;
}

.account-container {
  margin-top: 8px;
  margin-right: 32px;
  margin-bottom: 16px;
  margin-left: auto;
  float: right;
  text-align: right;
  height: 64px;
  width: 278px;
  color: #ffffff;
}
h5 {
  margin-top: 4px;
  margin-bottom: 4px;
}

h4 {
  font-size: 18px;
}

h1 {
  color: #d32f2f;
  font-size: 20px;
}
</style>

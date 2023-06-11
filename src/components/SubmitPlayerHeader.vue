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
                <form class="sign-up-form">
                  <div class="email-info">
                    <label for="email">Email</label><br />
                    <input
                      type="text"
                      id="email"
                      name="username"
                      placeholder="Email"
                      class="email"
                    />
                  </div>
                  <div class="username-info">
                    <label for="username">Username</label><br />
                    <input
                      type="text"
                      id="username"
                      name="password"
                      placeholder="Username"
                      class="username"
                    />
                  </div>
                  <div class="password-info">
                    <label>Password</label><br />
                    <input
                      type="text"
                      id="password"
                      placeholder="Password"
                      class="password"
                    />
                  </div>
                  <div class="submit-button">
                    <input type="submit" value="Submit" />
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
                <form class="sign-in-form">
                  <div class="username-info">
                    <label>Username</label><br />
                    <input
                      type="text"
                      placeholder="Username"
                      class="username"
                      id="username"
                    />
                  </div>
                  <div class="password-info">
                    <label>Password</label><br />
                    <input
                      type="text"
                      placeholder="Password"
                      class="password"
                      id="password"
                    />
                  </div>
                  <div class="submit-button">
                    <input type="submit" value="Submit" />
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

  public setOpenDialog(name?: string): void {
    if (this.openDialog === name) {
      this.openDialog = null;
    } else {
      this.openDialog = name;
    }
    this.isSignInOpen = this.openDialog === "signIn";
    this.isRegisterOpen = this.openDialog === "register";
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

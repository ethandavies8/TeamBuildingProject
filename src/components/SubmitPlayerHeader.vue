<template>
  <div class="Form-Page">
    <div class="header">
      <div class="diamond"></div>
      <h1 class="center">{{ msg }}</h1>
      <h4 class="sign-in">
        <input
          type="checkbox"
          id="sign-in-dropdown-visible"
          class="dropdown-checkbox"
        />
        <input
          type="checkbox"
          id="register-dropdown-visible"
          class="dropdown-checkbox"
        />
        <label for="register-dropdown-visible" class="create-an-account"
          >Create an account</label
        ><br />Already have an account?
        <label for="sign-in-dropdown-visible" class="sign-in">Sign in</label>
        <div class="dropdown-box-container">
          <div class="register-dropdown dropdown">register here</div>
          <div class="sign-in-dropdown dropdown">sign in here</div>
        </div>
      </h4>
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
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@use "../assets/style.scss";

.dropdown-checkbox {
  display: none;
}

.dropdown-box-container {
  position: relative;
}

.dropdown {
  position: absolute;
  height: 300px;
  width: 300px;
  transform: scale(0%);
  transition: transform 200ms ease-out;
  transform-origin: top right;
  background-color: palegreen;
}

input.dropdown-checkbox:checked ~ .dropdown-box-container .dropdown {
  transition: transform 200ms ease-in;
  transform: scale(100%);
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

.sign-in {
  margin-top: 16px;
  margin-right: 32px;
  margin-bottom: 16px;
  margin-left: auto;
  float: right;
  text-align: right;
  height: 48px;
  width: 278px;
  color: #ffffff;
}

h4 {
  font-size: 18px;
}

h1 {
  color: #d32f2f;
  font-size: 20px;
}
</style>

<template>
  <div class="Form-Page">
    <div class="header">
      <div class="container diamond-shape"></div>
      <h1 class="center">Submit Players</h1>
      <h4 class="sign-in">
        Create an account<br />Already have an account? Sign in
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

.diamond-shape {
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

h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

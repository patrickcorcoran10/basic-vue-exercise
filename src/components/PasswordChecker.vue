<template>
  <div>
    <label>Password Checker</label>
    <br>
    <input placeholder="Password" type="password" v-on:keyup.prevent="letterInput" v-model="password" v-bind:class="{badPassword : badPassword, goodPassword : goodPassword}">
    <br>
    <button @click.prevent="testSubmit">Test</button>
    </div>
</template>

<script>

export default {
  name: 'PasswordChecker',
  data() {
    return{
      password: "",
      goodPassword: false,
      badPassword: true,
      goodLength: false,
      hasUpper: false,
      hasLower: false,
      hasSpecial: false,
      containsPassword: false,
    }
  },
  methods: {
    letterInput() {
      console.log("input", this.password)
      if (this.password.length >= 16 && this.password.length <= 30) {
          this.goodLength = true;
      } else {
        this.goodLength = false;
      }
      // Upper Case Conditional
      if (/[A-Z]/.test(this.password)) {
        this.hasUpper = true
      } else {
        this.hasUpper = false;
      }
      // Lower Case Conditional
      if (/[a-z]/.test(this.password)) {
        this.hasLower = true
      } else {
        this.hasLower = false;
      }
      // Special Character Conditional
      if (/\W|_/.test(this.password)) {
        this.hasSpecial = true
      } else {
        this.hasSpecial = false
      }
      // Contains "password" Conditional
      if (this.password.includes("password")) {
        this.containsPassword = true
      } else {
        this.containsPassword = false
      }
      // Conditional for the Rendering
      if (this.goodLength && this.hasUpper && this.hasLower && this.hasSpecial && !this.containsPassword && this.password != 0) {
        this.goodPassword = true;
        this.badPassword = false;
      } else {
        this.goodPassword = false;
        this.badPassword = true;
      }
    },
    
    testSubmit() {
      if (this.goodPassword === true) {
        this.goodPassword = false;
        this.badPassword = true;
        this.password = '';
        alert("Success", this.password)
      } else {
        this.goodPassword = false;
        this.badPassword = true;
        this.password = '';
        alert("Failure")
      }
    }
  },
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 .badPassword, .badPassword:focus {
    outline: none !important;
    border:1px solid red;
    box-shadow: 0 0 10px #719ECE;
}
.goodPassword {
    outline: none !important;
    border:1px solid green;
    box-shadow: 0 0 10px #719ECE;
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

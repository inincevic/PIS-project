<template>
  <div class="registration">
    <h1 class="title_text">This is the sign up page</h1>
    <br />
    <br />
    <div class="container">
      <div class="row">
        <div class="col-sm"></div>
        <div class="col-sm">
          <form>
            <p class="plain_text">Username</p>
            <div class="form-group">
              <input
                type="username"
                v-model="credentials.username"
                class="form-control"
                id="exampleInputUsername"
                aria-describedby="usernameHelp"
                placeholder="Enter username"
              />
            </div>
            <br />
            <p class="plain_text">Email</p>
            <div class="form-group">
              <input
                type="email"
                v-model="credentials.email"
                class="form-control"
                id="exampleInputEmail1"
                aria-describedby="emailHelp"
                placeholder="Enter email"
              />
            </div>
            <br />
            <p class="plain_text">Password</p>
            <div class="form-group">
              <input
                type="password"
                v-model="credentials.password"
                class="form-control"
                id="exampleInputPassword1"
                placeholder="Password"
              />
            </div>
            <br />
            <p class="plain_text">Confirm Password</p>
            <div class="form-group">
              <input
                type="password"
                v-model="credentials.passwordConfirmation"
                class="form-control"
                id="exampleInputPassword2"
                placeholder="Confirm Password"
              />
            </div>
            <button type="button" @click="signup" class="btn btn-primary">
              Submit
            </button>
          </form>
        </div>
        <div class="col-sm"></div>
      </div>
    </div>
  </div>
</template>

<script>

import axios from "axios";

export default {
  name: "Registration",
  data() {
    return {
      credentials:{
        username: "",
        email: "",
        password: "",
        passwordConfirmation: "",
      }
    };
  },
  methods: {
    signup() {
      if (this.password == this.passwordConfirmation) {
        axios
          .post("https://pokeguesserproject.herokuapp.com/register", this.credentials)
          .then((response) => {
            console.log(response);
            if (response.data) {
              console.log(response.data);
              this.$router.push({
                name: "regsuccess",
              });
            } 
          });
      } else alert("Passwords do not match");
    },
  },
};
</script>

<style scoped>

.title_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 75px;
  letter-spacing: 3px;
}

.plain_text {
  color: black;
  font-family: "Unown", sans-serif;
  font-size: 35px;
}
</style>

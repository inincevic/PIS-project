<template>
  <div class="about">
    <h1 class="title_text">Log in using your credentials</h1>
    <br />
    <br />
    <div class="container">
      <div class="row">
        <div class="col-sm"></div>
        <div class="col-sm">
          <form @submit="checkCredentials()" action="#" onsubmit="return false">
            <div class="form-group">
              <label for="exampleInputEmail1" class="plain_text"
                >Email address</label
              >
              <input
                type="email"
                class="form-control"
                id="exampleInputEmail1"
                aria-describedby="emailHelp"
                placeholder="Enter email"
                v-model="loginCredentials.email"
              />
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1" class="plain_text"
                >Password</label
              >
              <input
                type="password"
                class="form-control"
                id="exampleInputPassword1"
                placeholder="Password"
                v-model="loginCredentials.password"
              />
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
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
  name: "Login",

  async mounted() {},

  methods: {
    async storeUser(user) {
      localStorage.setItem("username", user.username);
      localStorage.setItem("number_guessed", user.number_guessed);
      localStorage.setItem("favourite_pokemon", user.favourite_pokemon);
    },
    removeFromStorage() {
      localStorage.removeItem("username");
      localStorage.removeItem("number_guessed");
      localStorage.removeItem("favourite_pokemon");
    },
    checkCredentials() {
      axios
        .post("https://pokeguesserproject.herokuapp.com/login", this.loginCredentials)
        .then((response) => {
          if (response.data) {
            this.removeFromStorage();
            this.storeUser(response.data);
            this.$router.push({
              name: "profile",
            });
          } else {
            alert(
              "Incorrect credentials. Please try again. If you are not a user, please register."
            );
          }
        });
    },
  },

  data() {
    return {
      loginCredentials: {
        email: "",
        password: "",
      },
    };
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

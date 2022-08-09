<template>
  <div class="container">
    <!-- Uppermost row -> shows username, number guessed and the favourite Pokémon -->
    <div class="row row-upper">
      <h1 class="title_text">Welcome {{ userInfo.username }}</h1>
      <p class="plain_text">
        Number of guessed Pokémon: {{ userInfo.number_guessed }}
      </p>
      <p class="plain_text">
        Favourite Pokémon: {{ userInfo.favourite_pokemon }}
      </p>
    </div>

    <!-- Middle row -> button for setting Pokémon -->
    <div class="row row-middle">
      <div class="col-sm-6">
        <p class="sub_text">Set favourite Pokémon.</p>
        <button
          type="button"
          class="btn btn-success btn-lg btn-favourite"
        >
          <router-link to="/FavouriteSelection">Select</router-link>
        </button>
      </div>
      <div class="col-sm-6"></div>
    </div>

    <div class="row row-lower">
      <div class="col-sm-5">
        <p class="sub_text">List of all the Pokémon you guessed</p>
        <button type="button" class="btn btn-success btn-lg btn-list">
          <router-link to="/GuessedList">List</router-link>
        </button>
      </div>
      <div class="col-sm-2"></div>
      <div class="col-sm-5">
        <p class="sub_text">Pokémon guessing</p>
        <button type="button" class="btn btn-success btn-lg btn-guess">
          <router-link to="/UserGuess">Guess</router-link>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Profile",
  data() {
    return {
      userInfo: {
        username: "",
        number_guessed: "",
        favourite_pokemon: "",
      },
    };
  },
  methods: {
    async replace_name() {
      if (localStorage.getItem("favourite_pokemon") != "") {
        await axios
          .post("https://pokeguesserproject.herokuapp.com/favouritename", this.userInfo)
          .then(async (response) => {
            localStorage.removeItem("favourite_pokemon");
            localStorage.setItem("favourite_pokemon", response.data);
          });
      } else {
        this.userInfo.favourite_pokemon = "Not set.";
      }
    },
  },
  async created() {
    this.userInfo.username = localStorage.getItem("username");
    this.userInfo.number_guessed = localStorage.getItem("number_guessed");
    this.userInfo.favourite_pokemon = localStorage.getItem("favourite_pokemon");
    await this.replace_name();
    this.userInfo.favourite_pokemon = localStorage.getItem("favourite_pokemon");
  },
};
</script>

<style scoped>

.row-lower {
  min-height: calc(25vh - 100px);
}

.row-middle {
  min-height: calc(35vh - 100px);
}

.row-upper {
  min-height: calc(40vh - 100px);
  text-align: left;
}

.btn-guess {
  margin: 1em;
  font-family: "Pokemon Solid";
  color: #2a75bb;
  background-color: #ffcb05;
}

.btn-list {
  margin: 1em;
  font-family: "Pokemon Solid";
  color: #2a75bb;
  background-color: #ffcb05;
}

.btn-favourite {
  margin: 1em;
  font-family: "Pokemon Solid";
  color: #2a75bb;
  background-color: #ffcb05;
}

.title_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 75px;
  letter-spacing: 4px;
}

.plain_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 35px;
  letter-spacing: 3px;
  margin-top: 2%;
}
.sub_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 25px;
  letter-spacing: 3px;
}
</style>

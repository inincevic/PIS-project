<template>
  <!-- Information row -->
  <div class="row row-upper">
    <div class="title_text">Pokémon guessed by {{ username }}</div>
    <div class="plain_text">
      Number of guessed Pokémon: {{ number_guessed }}
    </div>
  </div>
  <!-- Display box -->
  <div class="row row-middle">
    <div class="text_box">
      <div class="text_in_box">
        <p v-for="pokemon in guessed_pokemon" :key="pokemon">
          {{ pokemon.pokemon_name }}
          <br />
          -------------------------------------------------------------
        </p>
      </div>
    </div>
  </div>
  <!-- Button -->
  <div class="row row-lower">
    <div class="col-xs-4 btn-col"></div>
    <div class="col-xs-4 btn-col"></div>
    <div class="col-xs-4 btn-col">
      <div class="sub_text">Return to profile</div>
      <button
        type="button"
        class="btn btn-success btn-lg"
        style="
          margin: 1em;
          font-family: 'Pokemon Solid';
          color: #2a75bb;
          background-color: #ffcb05;
        "
      >
        <router-link to="/profile">Return</router-link>
      </button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Profile",
  data() {
    return {
      username: "",
      number_guessed: "",
      guessed_pokemon: [],
    };
  },
  methods: {
    async getFoundPokemon() {
      await axios
        .post("https://pokeguesserproject.herokuapp.com/guessedpokemon", {
          username: this.username,
        })
        .then(async (response) => {
          this.guessed_pokemon = response.data;
          console.log(this.guessed_pokemon);
          if (this.guessed_pokemon[0] == null) {
            this.guessed_pokemon[0] = "This user has yet to guess any Pokémon";
          }
        });
    },
  },
  created() {
    this.username = localStorage.getItem("username");
    this.number_guessed = localStorage.getItem("number_guessed");
    this.getFoundPokemon();
  },
};
</script>

<style scoped>
.row-lower {
  min-height: calc(25vh - 100px);
}

.row-middle {
  min-height: calc(55vh - 100px);
}

.row-upper {
  min-height: calc(20vh - 100px);
  text-align: left;
}

.title_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 60px;
  letter-spacing: 3px;
  text-align: left;
  margin-left: 3%;
}

.plain_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 35px;
  text-align: left;
  margin-left: 4%;
  margin-top: 1%;
  letter-spacing: 3px;
}
.sub_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 25px;
  letter-spacing: 3px;
}
.text_box {
  background-color: darkgray;
  text-align: left;
  letter-spacing: 3px;
  margin-left: 4%;
  margin-right: 4%;
  margin-top: 3%;
  min-height: 40vh;
}
.text_in_box {
  font-family: "Pokemon Solid", sans-serif;
  font-size: 30px;
  margin-left: 1%;
}
</style>

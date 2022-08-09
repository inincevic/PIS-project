<template>
  <div class="about">
    <div class="row row-upper">
      <h1 class="title_text">The Pokémon is</h1>
    </div>
    <!-- Display row -->
    <div class="row row-middle">
      <div>
        <p class="normal_text">
          Name: {{ pokemon.name }}
          <br />
          Type: {{ pokemon.types.type_one }}, {{ pokemon.types.type_two }}
          <br />
          Colours: {{ pokemon.colours.colour_one }},
          {{ pokemon.colours.colour_two }}
          <br />
          Form: {{ pokemon.form }}
          <br />
          Evolution method: {{ pokemon.evolution_method }}
          <br />
          Regional variant: {{ pokemon.regional_variant }}
          <br />
          Dex entry: {{ pokemon.dex_entry }}
          <br />
          Base stat total: {{ pokemon.base_state_total }}
        </p>
      </div>
    </div>
    <!-- Return to profile button -->
    <div class="row attribute-row">
      <div class="col-sm-4"></div>
      <div class="col-sm-4"></div>
      <div class="col-sm-4">
        <div class="sub_text">
          Return to Profile
          <br />
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
        <div class="col-sm-4"></div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "foundUser",
  data() {
    return {
      pokemon: {
        name: "",
        types: {
          type_one: "",
          type_two: "",
        },
        colours: {
          colour_one: "",
          colour_two: "",
        },
        form: "",
        evolution_method: "",
        regional_variant: "",
        dex_entry: "",
        base_state_total: "",
      },
    };
  },
  created() {
    this.pokemon.name = localStorage.getItem("foundPokemonName");
    this.pokemon.types.type_one = localStorage.getItem("foundPokemonTypeOne");
    this.pokemon.types.type_two = localStorage.getItem("foundPokemonTypeTwo");
    this.pokemon.colours.colour_one = localStorage.getItem(
      "foundPokemonColourOne"
    );
    this.pokemon.colours.colour_two = localStorage.getItem(
      "foundPokemonColourTwo"
    );
    this.pokemon.form = localStorage.getItem("foundPokemonStage");
    this.pokemon.evolution_method = localStorage.getItem(
      "foundPokemonEvolutionMethod"
    );
    this.pokemon.regional_variant = localStorage.getItem(
      "foundPokemonRegionalVariant"
    );
    this.pokemon.dex_entry = localStorage.getItem("foundPokemonEntry");
    this.pokemon.base_state_total = localStorage.getItem("foundPokemonBST");
  },
};
</script>

<style scoped>

.row-lower {
  min-height: calc(25vh - 100px);
}

.row-middle {
  min-height: calc(35vh - 100px);
  margin-top: 1%;
  margin-left: 4%;
}

.row-upper {
  min-height: calc(10vh - 100px);
  text-align: left;
  margin-left: 4%;
}

.title_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 75px;
  letter-spacing: 3px;
}

.plain_text {
  color: #ffcb05;
  font-family: "Unown", sans-serif;
  font-size: 50px;
}

.normal_text {
  color: #ffcb05;
  font-family: "Times New Roman", Times, serif;
  text-align: left;
  font-size: 35px;
}

.sub_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 25px;
  letter-spacing: 3px;
}
</style>

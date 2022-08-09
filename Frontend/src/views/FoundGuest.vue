<template>
  <div class="about">
    <h1 class="title_text">The Pokémon is</h1>
    <br />
    <div class="display_div">
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

    <button
      type="button"
      class="btn btn-success btn-lg"
      style="
        margin: 1em;
        font-size: 25px;
        font-family: 'Pokemon Solid';
        color: #2a75bb;
        background-color: #ffcb05;
      "
    >
      <router-link to="/">Home</router-link>
      <!-- Note: will have to create this page with display once database and backend communication are complete -->
    </button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "FoundGuest",
  
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

.display_div {
  margin-left: 200px;
}
</style>

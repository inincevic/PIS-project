<template>
  <div class="container-fluid">
    <!-- Primary type row -->
    <div class="row attribute-row">
      <div class="col-sm-4">
        <p class="normal_text">Primary type*</p>
      </div>
      <!-- Dropdown menu -->
      <div class="col-sm-4">
        <form
          @submit="sendPokemonCredentials()"
          action="#"
          onsubmit="return false"
        >
          <div class="input-group mb-3">
            <div class="input-group-prepend">
              <label class="inputPrimaryType"></label>
            </div>
            <select
              class="custom-select"
              id="inputGroupSelect01"
              style="width: 400px; height: 30px"
              v-model="enteredAtributes.type_one"
            >
              <option selected></option>
              <option v-for="type in attributes_database.types" :key="type">
                {{ type.type_name }}
              </option>
            </select>
          </div>
        </form>
      </div>
      <!-- Explanation -->
      <div class="col-sm-4">
        <p class="explanation">
          Select what the primary type of the Pokémon is. <br />
        </p>
      </div>
    </div>

    <!-- Secondary type row -->
    <div class="row attribute-row">
      <div class="col-sm-4">
        <p class="normal_text">Secondary type</p>
      </div>
      <!-- Dropdown menu -->
      <div class="col-sm-4">
        <form
          @submit="sendPokemonCredentials()"
          action="#"
          onsubmit="return false"
        >
          <div class="input-group mb-3">
            <div class="input-group-prepend">
              <label class="inputPrimaryType"></label>
            </div>
            <select
              class="custom-select"
              id="inputGroupSelect01"
              style="width: 400px; height: 30px"
              v-model="enteredAtributes.type_two"
            >
              <option selected></option>
              <option v-for="type in attributes_database.types" :key="type">
                {{ type.type_name }}
              </option>
            </select>
          </div>
        </form>
      </div>
      <!-- Explanation -->
      <div class="col-sm-4">
        <p class="explanation">
          Type what the secondary type of the Pokémon is. <br />
        </p>
      </div>
    </div>

    <!-- Primary Colour row -->
    <div class="row attribute-row">
      <div class="col-sm-4">
        <p class="normal_text">Primary colour*</p>
      </div>
      <!-- Dropdown menu -->
      <div class="col-sm-4">
        <form
          @submit="sendPokemonCredentials()"
          action="#"
          onsubmit="return false"
        >
          <div class="input-group mb-3">
            <div class="input-group-prepend">
              <label class="inputPrimaryType"></label>
            </div>
            <select
              class="custom-select"
              id="inputGroupSelect01"
              style="width: 400px; height: 30px"
              v-model="enteredAtributes.colour_one"
            >
              <option selected></option>
              <option
                v-for="colour in attributes_database.colours"
                :key="colour"
              >
                {{ colour.colour_name }}
              </option>
            </select>
          </div>
        </form>
      </div>
      <!-- Explanation -->
      <div class="col-sm-4">
        <p class="explanation">
          Type what the dominant of the Pokémon is. <br />
        </p>
      </div>
    </div>

    <!-- Secondary Colour row -->
    <div class="row attribute-row">
      <div class="col-sm-4">
        <p class="normal_text">Secondary colour</p>
      </div>
      <!-- Dropdown menu -->
      <div class="col-sm-4">
        <form
          @submit="sendPokemonCredentials()"
          action="#"
          onsubmit="return false"
        >
          <div class="input-group mb-3">
            <div class="input-group-prepend">
              <label class="inputPrimaryType"></label>
            </div>
            <select
              class="custom-select"
              id="inputGroupSelect01"
              style="width: 400px; height: 30px"
              v-model="enteredAtributes.colour_two"
            >
              <option selected></option>
              <option
                v-for="colour in attributes_database.colours"
                :key="colour"
              >
                {{ colour.colour_name }}
              </option>
            </select>
          </div>
        </form>
      </div>
      <!-- Explanation -->
      <div class="col-sm-4">
        <p class="explanation">
          Type what the second dominant colour of the Pokémon is. <br />
        </p>
      </div>
    </div>

    <!-- Stage row -->
    <div class="row attribute-row">
      <div class="col-sm-4">
        <p class="normal_text">Stage</p>
      </div>
      <!-- Input field  -->
      <div class="col-sm-4">
        <form>
          <div class="form-group">
            <label for="inputForm" class="plain_text"></label>
            <input
              type="stage"
              class="form-control"
              style="width: 400px; height: 30px"
              id="inputForm"
              aria-describedby="emailHelp"
              placeholder="Enter form"
              v-model="enteredAtributes.stage"
            />
          </div>
        </form>
      </div>
      <!-- Explanation -->
      <div class="col-sm-4">
        <p class="explanation">
          Type what is the form of this Pokémon. <br />
          (Base form, 1st stage, 2nd stage)
        </p>
      </div>
    </div>

    <!-- Evolution method row -->
    <div class="row attribute-row">
      <div class="col-sm-4">
        <p class="normal_text">Evolution method</p>
      </div>
      <!-- Dropdown menu -->
      <div class="col-sm-4">
        <form
          @submit="sendPokemonCredentials()"
          action="#"
          onsubmit="return false"
        >
          <div class="input-group mb-3">
            <div class="input-group-prepend">
              <label class="inputEvolutionMethod"></label>
            </div>
            <select
              class="custom-select"
              id="inputGroupSelect01"
              style="width: 400px; height: 30px"
              v-model="enteredAtributes.evolution_method"
            >
              <option selected></option>
              <option
                v-for="method in attributes_database.evolution_methods"
                :key="method"
              >
                {{ method.method_name }}
              </option>
            </select>
          </div>
        </form>
      </div>
      <!-- Explanation -->
      <div class="col-sm-4">
        <p class="explanation">
          Type what method is needed for this Pokémon to reach this stage from
          it's previous stage. <br />
        </p>
      </div>
    </div>

    <!-- Regional variant -->
    <div class="row attribute-row">
      <div class="col-sm-4">
        <p class="normal_text">Regional variant</p>
      </div>
      <!-- Dropdown menu -->
      <div class="col-sm-4" style="align-content: center">
        <form
          @submit="sendPokemonCredentials()"
          action="#"
          onsubmit="return false"
        >
          <div class="input-group mb-3">
            <div class="input-group-prepend">
              <label class="inputEvolutionMethod"></label>
            </div>
            <select
              class="custom-select"
              style="width: 400px; height: 30px"
              id="inputGroupSelect01"
              v-model="enteredAtributes.regional_variant"
            >
              <option selected></option>
              <option
                v-for="variant in attributes_database.forms"
                :key="variant"
              >
                {{ variant.variant_name }}
              </option>
            </select>
          </div>
        </form>
      </div>
      <!-- Explanation -->
      <div class="col-sm-4">
        <p class="explanation">
          Type what regional variant this Pokémon is. <br />
        </p>
      </div>
    </div>

    <!-- Base stat total row -->
    <div class="row attribute-row">
      <div class="col-sm-4">
        <p class="normal_text">Base stat total</p>
      </div>
      <!-- Input field -->
      <div class="col-sm-4">
        <form>
          <div class="form-group">
            <label for="inputBaseStatTotal" class="plain_text"></label>
            <input
              type="baseStatTotal"
              class="form-control"
              style="width: 400px; height: 30px"
              id="inputBaseStatTotal"
              aria-describedby="emailHelp"
              placeholder="Enter base stat total"
              v-model="enteredAtributes.base_stat_total"
            />
          </div>
        </form>
      </div>
      <!-- Explanation -->
      <div class="col-sm-4">
        <p class="explanation">Enter this Pokémon's base stat total.</p>
      </div>
    </div>

    <!-- Button row -->
    <div class="row attribute-row">
      <div class="col-sm-4"></div>
      <div class="col-sm-4">
        <button
          type="submit"
          class="btn btn-success btn-lg"
          style="
            margin: 1em;
            font-family: 'Pokemon Solid';
            color: #2a75bb;
            background-color: #ffcb05;
          "
          @click="sendPokemonCredentials()"
        >
          Continue
        </button>
      </div>
      <div class="col-sm-4"></div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "GuestGuess",

  methods: {
    //adding found Pokémon's data into localhost
    async setPokemon(response) {
      localStorage.setItem("foundPokemonNumber", response.data.dex_number);
      localStorage.setItem("foundPokemonName", response.data.pokemon_name);
      localStorage.setItem(
        "foundPokemonTypeOne",
        response.data.types[0].type_id
      );
      if (response.data.types.length > 1) {
        localStorage.setItem(
          "foundPokemonTypeTwo",
          response.data.types[1].type_id
        );
      }
      localStorage.setItem(
        "foundPokemonColourOne",
        response.data.colours[0].colour_id
      );
      if (response.data.colours.length > 1) {
        localStorage.setItem(
          "foundPokemonColourTwo",
          response.data.colours[1].colour_id
        );
      }
      localStorage.setItem("foundPokemonStage", response.data.stage);
      localStorage.setItem(
        "foundPokemonEvolutionMethod",
        response.data.evolution_method
      );
      localStorage.setItem("foundPokemonRegionalVariant", response.data.form);
      localStorage.setItem("foundPokemonBST", response.data.base_stat_total);
      localStorage.setItem("foundPokemonEntry", response.data.dex_entry);
    },

    //emptying fields from storage
    removeFromStorage() {
      localStorage.removeItem("foundPokemonNumber");
      localStorage.removeItem("foundPokemonName");
      localStorage.removeItem("foundPokemonTypeOne");
      localStorage.removeItem("foundPokemonTypeTwo");
      localStorage.removeItem("foundPokemonColourOne");
      localStorage.removeItem("foundPokemonColourTwo");
      localStorage.removeItem("foundPokemonStage");
      localStorage.removeItem("foundPokemonEvolutionMethod");
      localStorage.removeItem("foundPokemonRegionalVariant");
      localStorage.removeItem("foundPokemonBST");
      localStorage.removeItem("foundPokemonEntry");
    },

    //getting attributes from the database
    async getAttributes() {
      await axios
        .get("https://pokeguesserproject.herokuapp.com/getattributes")
        .then((response) => {
          this.attributes_database = response.data;
        });
    },

    //finding a Pokémon with given credentials
    sendPokemonCredentials() {
      if (
        this.enteredAtributes.type_one === "" ||
        this.enteredAtributes.colour_one === ""
      ) {
        alert("Primary type and primary colour need to be provided.");
        return;
      }
      axios
        .post("https://pokeguesserproject.herokuapp.com/findpokemon", this.enteredAtributes)
        .then((response) => {
          console.log("recieved response");
          console.log(response);
          if (response.data) {
            this.removeFromStorage();
            this.setPokemon(response);
            this.$router.push({
              name: "foundguest",
            });
          } else {
            alert("404 Pokémon not found");
          }
          //push to 404 pokemon not found
        });
    },
  },

  created() {
    this.getAttributes();
  },

  data() {
    return {
      enteredAtributes: {
        type_one: "",
        type_two: "",
        colour_one: "",
        colour_two: "",
        stage: "",
        evolution_method: "",
        regional_variant: "",
        base_stat_total: "",
      },
      attributes_database: {
        types: [],
        colours: [],
        evolution_methods: [],
        forms: [],
      },
    };
  },
};
</script>

<style scoped>
.attribute-row {
  min-height: calc(10vh - 100px);
}

.dropdown-menu {
  left: 50%;
  right: auto;
  text-align: center;
  transform: translate(-50%, 0);
}

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

.normal_text {
  color: #ffcb05;
  font-family: "Times New Roman", Times, serif;
  font-size: 30px;
}

.explanation {
  color: #ffcb05;
  font-family: "Times New Roman", Times, serif;
  font-size: 20px;
}
</style>

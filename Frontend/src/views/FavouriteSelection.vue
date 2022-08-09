<template>
  <div class="container">
    <!-- Title -->
    <div class="row row-upper">
      <h1 class="title_text">
        {{ userInfo.username }}, please write the name of your favourite Pokémon
      </h1>
    </div>
    <!-- Input field -->
    <div class="row row-middle">
      <p class="plain_text">
        Current favourite Pokémon: {{ userInfo.favourite_pokemon }}
      </p>
      <div class="form-group">
        <div class="col-xs-8">
          <input
            type="email"
            class="form-control"
            id="exampleInputPokemon"
            placeholder="New favourite Pokémon"
            v-model="userInfo.new_favourite_pokemon"
          />
        </div>
      </div>
    </div>
    <!-- Buttons -->
    <div class="row row-lower">
      <div class="col-xs-2"></div>
      <div class="col-xs-4 btn-col">
        <div class="sub_text">Save your selection</div>
        <button
          type="button"
          class="btn btn-success btn-lg"
          style="
            margin-left: 1000 px;
            margin-top: 20px;
            font-family: 'Pokemon Solid';
            color: #2a75bb;
            background-color: #ffcb05;
          "
          @click="updateFavourite()"
        >
          <router-link to="/profile">Save</router-link>
        </button>
      </div>
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
      <div class="col-xs-2"></div>
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
        favourite_pokemon: "",
        new_favourite_pokemon: "",
      },
      response: "",
    };
  },
  created() {
    this.userInfo.username = localStorage.getItem("username");
    this.userInfo.favourite_pokemon = localStorage.getItem("favourite_pokemon");
    if (this.userInfo.favourite_pokemon == "") {
      this.userInfo.favourite_pokemon = "Not set.";
    }
  },
  methods: {
    async favouriteName() {},
    async updateFavourite() {
      axios
        .put("https://pokeguesserproject.herokuapp.com/updatefavourite", this.userInfo)
        .then((response) => {
          if (response.data) {
            alert(
              "New favourite Pokémon has been set. It will show up on your profile after your next login."
            );
          } else {
            alert(
              "That Pokémon is either your current favourite or not a part of this database. Please try again."
            );
          }
        });
    },
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

.btn-col{
  align-content: center;
  text-align: center;
}

.title_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 55px;
  letter-spacing: 4px;
}

.plain_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 35px;
  text-align: left;
  letter-spacing: 3px;
}

.sub_text {
  color: #ffcb05;
  font-family: "Pokemon Solid", sans-serif;
  font-size: 25px;
  letter-spacing: 3px;
}
</style>

<template>
  <div class="contsiner">
    <b-row align-h="center" cols="4">
      <b-form-select
        v-model="searchmet"
        :options="searchOption"
      ></b-form-select>
    </b-row>

    <b-row align-h="center" v-if="searchmet == 1">
      <b-col cols="2">
        <b-form-input v-model="keyword" placeholder="Enter name"></b-form-input>
      </b-col>
      <b-col cols="4" md="auto">
        <b-button @click="searchData()">Search</b-button>
      </b-col>
    </b-row>
    <b-row align-h="center" v-if="searchmet == 2">
      <b-col cols="2">
        <b-form-select v-model="selected" :options="options"></b-form-select>
      </b-col>
      <b-col cols="4" md="auto">
        <b-button @click="searchSeason()">Search</b-button>
      </b-col>
    </b-row>
    {{ result }}
    <!--<b-button pill variant="outline-secondary"> Search</b-button>-->
    <!--<b-card-group columns>
      <b-card
        v-for="data in result"
        :key="data.mal_id"
        :title="data.title"
        :img-src="data.image_url"
        :img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem"
        class="mb-2"
      >
        <b-card-text>{{ data.synopsis }}</b-card-text>
        <b-button :href="data.url" variant="primary">Go somewhere</b-button>
      </b-card>
    </b-card-group>-->
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      result: null,
      keyword: "",
      selected: null,
      searchmet: null,
      options: [
        { value: null, text: "Please select a house" },
        { value: "gryffindor", text: "Gryffindor" },
        { value: "hufflepuff", text: "Hufflepuff" },
        { value: "ravenclaw", text: "Ravenclaw" },
        { value: "slytherin", text: "Slytherin" },
      ],
      searchOption: [
        { value: null, text: "Please select search method" },
        { value: 1, text: "Search by name" },
        { value: 2, text: "select the desired house." },
      ],
    };
  },
  methods: {
    searchData() {
      axios
        .get(
          "https://www.potterapi.com/v1/characters?key=$2a$10$y2st9DZ203ErCMHLEu1oAO.h/2GetoanHRC8xAi2hGjF6D8Y07JFa" +
            this.keyword
        )
        .then(
          (response) => (
            (this.result = response.data.results),
            (this.load = true),
            (this.currentPage = 1)
          )
        )
        .catch((err) => console.log(err));
    },
    searchSeason() {
      axios
        .get(
          "https://www.potterapi.com/v1/houses?key=$2a$10$y2st9DZ203ErCMHLEu1oAO.h/2GetoanHRC8xAi2hGjF6D8Y07JFa" +
            this.selected
        )
        .then(
          (response) => (
            (this.result = response.data.results),
            (this.load = true)
           
          )
        )
        .catch((err) => console.log(err));
    },
  },
watch: {
    searchmet: function (val) {
      if (val == 3) {
        this.upcoming();
      }
    },
  },

};
</script>

<style>
</style>

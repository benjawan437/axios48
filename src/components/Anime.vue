<template>
  <div class="contsiner">
      <div align="center">
        <b-form-input
          v-model="keyword"
          class="sea"
          placeholder="Enter a movie title"
        ></b-form-input>
        <b-button pill variant="outline-dark" @click="searchData()"
          >Search Anime</b-button
        >
      </div>

    <b-card-group columns>
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
    </b-card-group>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      result: null,
      keyword: "",
    };
  },
  methods: {
    searchData() {
      axios
        .get(
          "https://api.jikan.moe/v3/search/anime?q=" + this.keyword + "&page=1"
        )
        .then((response) => {
          this.result = response.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
<style>
.sea {
  width: 30rem;
}
</style>
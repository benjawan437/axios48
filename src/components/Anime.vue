<template>
  <div class="contsiner">
    <div align="center">
      <b-form-input
        v-model="keyword"
        class="sea"
        placeholder="Enter a movie title"
      ></b-form-input>
        <b-button pill variant="warning" @click="search()">Search</b-button>
    </div>
    <b-card-group class="mt-2" columns>
      <b-card
        class="mb-2"
        v-for="data in result"
        :key="data.imdbID"
        :title="data.Title"
        :img-src="data.Poster"
        :img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem"
      >
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
      data: "",
    };
  },
  methods: {
    search() {
      axios
        .get("http://www.omdbapi.com/?s=" + this.keyword + "&apikey=409a3997")
        .then((response) => {
          this.result = response.data.Search;
          console.log(this.result);
        })
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
.sea {
  width: 30rem;
}
</style>
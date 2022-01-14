<template>
  <div>
    <v-data-table
      :headers="headers"
      :items.sync="movies"
      :items-per-page="10"
      class="elevation-7 mt-10"
    >
    </v-data-table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "IndexPage",
  data() {
    return {
      movies: [],
      headers: [
        {
          text: "İsim",
          align: "start",
          sortable: false,
          value: "name",
        },
        { text: "Yapımcı", value: "producer" },
        { text: "Süre (dk)", value: "runtime" },
        { text: "Imbd Puanı", value: "popularity" },
        { text: "Dil", value: "language" },
      ],
    };
  },
  async fetch() {
    await this.getData();
  },
  methods: {
    async getData() {
      return new Promise((resolve, reject) => {
        axios.get("http://localhost:3000/movies").then((res) => {
          this.movies = res.data;

          resolve();
        }).catc;
      });
    },
  },
};
</script>

<style></style>

<template>
  <v-form
    ref="form"
    class="mt-15 pt-3 form-style elevation-7 orange lighten-4"
    v-model="valid"
    lazy-validation
  >
    <v-subheader>Create Movies</v-subheader>
    <v-row>
      <v-col cols="6" class="pa-15">
        <v-text-field
          v-model="movie.name"
          label="Film Adı"
          required
          color="error"
        ></v-text-field>
        
        <v-text-field
          v-model="movie.producer"
          label="Film Yapımcısı"
          required
          color="error"
        ></v-text-field>

        <v-text-field
          v-model="movie.language"
          label="Film Yayın Dili"
          required
          color="error"
        ></v-text-field>
        <v-btn outlined class="mr-4 mt-15" @click="addMovie"> Film Ekle </v-btn>
        <v-btn outlined class="mr-4 mt-15" @click="clearInputs">
          Temizle
        </v-btn>
      </v-col>
      <v-col cols="6" class="pa-15">
        <v-text-field
          v-model="movie.popularity"
          label="Filme puanın.. (10/?)"
          required
          color="error"
        ></v-text-field>

        <v-text-field
          v-model="movie.runtime"
          label="Film süresi (Dk).."
          required
          color="error"
        ></v-text-field>

        <v-text-field
          v-model="movie.url"
          label="Bu alana film image'ini url olarak ekleyebilirsiniz."
          required
          color="error"
        ></v-text-field>
      </v-col>
      <v-card v-if="trueCheck" class="ml-15 d-flex align-center px-10" style="color:white" color="blue" width="400" height="50">  Film Eklendi... <v-spacer></v-spacer> <v-icon color="white">mdi-check-all</v-icon></v-card>
    </v-row>
  </v-form>
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
    valid: true,
    movie: {
      name: "",
      producer: "",
      language: "",
      popularity: "",
      runtime: "",
      url: "",
    },
     trueCheck:false
  }),

  methods: {
    addMovie() {
      axios
        .post("http://localhost:3000/movies", this.movie)
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
      this.movie.name = "";
      this.movie.producer = "";
      this.movie.language = "";
      this.movie.popularity = "";
      this.movie.runtime = "";
      this.movie.url = "";
      this.trueCheck=true
      setTimeout(() => this.trueCheck = false, 2000);
    },
    clearInputs() {
      this.movie.name = "";
      this.movie.producer = "";
      this.movie.language = "";
      this.movie.popularity = "";
      this.movie.runtime = "";
      this.movie.url = "";
    }
  },
};
</script>
<style>
.form-style {
  border-radius: 10px;
}
</style>

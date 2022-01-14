<template>
  <div>
    <v-card class="elevation-7">
      <v-list class="mt-15 blue lighten-5">
        <v-subheader>Edit Movies</v-subheader>
        <v-list-item-group>
          <v-list-item v-for="(movie, index) in movies" :key="index">
            {{ movie.name }}
            <v-spacer />
            <v-dialog v-model="dialog" width="500">
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  class="mr-5 amber lighten-3"
                  small
                  v-bind="attrs"
                  v-on="on"
                  @click.prevent="getMovie(movie.id)"
                >
                  <v-icon>mdi-pencil</v-icon>
                </v-btn>
              </template>

              <v-card class="pa-15">
                <v-text-field
                  label="Film Adı"
                  v-model="updateMovie.name"
                ></v-text-field>
                <v-text-field
                  label="Filmin Yapımcısı"
                  v-model="updateMovie.producer"
                ></v-text-field>
                <v-text-field
                  label="Filmin Dili"
                  v-model="updateMovie.language"
                ></v-text-field>
                <v-text-field
                  label="Filmin Puanı"
                  v-model="updateMovie.popularity"
                ></v-text-field>
                <v-text-field
                  label="Filmin Süresi (Dk)"
                  v-model="updateMovie.runtime"
                ></v-text-field>
                <v-img
                  :src="updateMovie.url"
                  max-height="150"
                  class="mb-10"
                ></v-img>
                <v-btn class="red lighten-3" @click="dialog = false"
                  >İptal</v-btn
                >
                <v-btn
                  class="blue lighten-3"
                  @click="updatedMovie(updateMovie.id)"
                  >Güncelle</v-btn
                >
              </v-card>
            </v-dialog>
            <v-dialog v-model="dialog2" persistent max-width="500">
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  small
                  class="red lighten-3"
                  dark
                  v-bind="attrs"
                  v-on="on"
                  @click="selectedMovie(movie.id)"
                >
                  <v-icon>mdi-delete</v-icon>
                </v-btn>
              </template>
              <v-card>
                <v-card-title class="mb-10"> Emin misin? </v-card-title>

                <v-card-subtitle>
                  {{ selectmovie.name }} silinmek üzere ?
                </v-card-subtitle>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn
                    color="red darken-1"
                    text
                    @click="deletedMovie(selectmovie.id)"
                  >
                    Sil
                  </v-btn>
                  <v-btn color="green darken-1" text @click="dialog2 = false">
                    İptal Et
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-card>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      movies: [],
      dialog: false,
      dialog2: false,
      updateMovie: {},
      selectmovie: {},
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
        }).catch;
      });
    },
    getMovie(id) {
      axios.get("http://localhost:3000/movies/" + id).then((resp) => {
        const data = resp.data;
        this.updateMovie = data;
      });
    },
    updatedMovie(id) {
      axios
        .put("http://localhost:3000/movies/" + id, this.updateMovie)
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
      this.dialog = false;
      this.getData();
    },
    selectedMovie(id) {
      axios.get("http://localhost:3000/movies/" + id).then((resp) => {
        const data = resp.data;
        this.selectmovie = data;
      });
    },
    deletedMovie(id) {
      axios
        .delete("http://localhost:3000/movies/" + id)
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
      this.getData();
      this.dialog2 = false;
    },
  },
};
</script>

<style></style>

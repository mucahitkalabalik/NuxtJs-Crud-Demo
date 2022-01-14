<template>
  <div>
    <v-app-bar elevation="4" shaped color="red">
      <nuxt-link to="/" class="logotext"
        ><v-icon color="white" large>mdi-movie-filter-outline</v-icon> Movies
        Crud Demo</nuxt-link
      >
      <v-spacer></v-spacer>
      <nuxt-link to="/create" class="header-list-item"
        ><v-icon color="white" medium>mdi-pencil</v-icon> Create</nuxt-link
      >
      <nuxt-link to="/edit" class="header-list-item"
        ><v-icon color="white" medium>mdi-circle-edit-outline</v-icon>
        Edit</nuxt-link
      >
    </v-app-bar>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.logotext {
  text-decoration: none;
  color: white;
  font-size: 1.5rem;
}
.header-list-item {
  text-decoration: none;
  color: white;
  font-size: 1.3rem;
  margin-right: 1rem;
}
@media only screen and (max-width: 425px) {
  .logotext{
    font-size: 1rem;
  }
  .header-list-item {

  font-size: .8rem;

}
}
</style>

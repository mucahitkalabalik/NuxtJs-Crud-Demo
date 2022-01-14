<template>
 <v-card min-height="200" color="red" class="d-flex align-center justify-center">
   <nuxt-link tag="v-btn" class="mr-5 ml-5 red accent-2" style="color:white"  to="/"> Home Page </nuxt-link>
   <nuxt-link tag="v-btn" class="mr-5 red accent-2" style="color:white" to="/create"> Create Page</nuxt-link>
   <nuxt-link tag="v-btn" class="mr-5 red accent-2" style="color:white" to="/edit"> Edit Page</nuxt-link>
   <v-spacer></v-spacer>
   <v-card-subtitle class="white"> <a href="https://github.com/mucahitkalabalik" target="_blank" class="link mr-15"> Github:mucahit.kalabalik</a></v-card-subtitle>
 </v-card>
</template>

<script>
export default {};
</script>

<style>
.link{
  text-decoration: none;
  color: black !important;
}
</style>

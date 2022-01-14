<template>
  <v-app style="  background-image: url('https://images.unsplash.com/photo-1518655048521-f130df041f66?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80')">
    <appheader />
    <v-container>
      <nuxt class="nuxt" />
    </v-container>
          <appfooter />
  </v-app>
</template>

<script>
import appheader from "../components/appheader.vue";
import appfooter from "../components/appfooter.vue";
export default {
  components: {
    appheader,
    appfooter,
  },
};
</script>

<style>
.nuxt {
  min-height: 62vh;
  margin-bottom: 6rem;
  padding-top: 6rem;
}
</style>

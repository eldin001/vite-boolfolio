<template>
  <AppHeader />
  <main class="container">
    <router-view  :key="$route.path"></router-view>
  </main>
</template>

<script>
import { store } from "./store";
import AppHeader from "./components/AppHeader.vue";
import axios from "axios";
export default {
  name: 'App',
  data() {
    return {
        store,
        projects: []
    }
  },
  methods: {
    getAllProjects() {
      axios.get(this.store.apiBaseUrl+'/projects').then((res) => {
console.log(res.data);
      })
    }
  },
  mounted() {
    this.getAllProjects();
  },
  components: {
    AppHeader
  },
}
</script>

<style lang="scss" scoped>
@use "./assets/styles/partials/variables" as *;
</style>
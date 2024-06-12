<template>
  <AppHeader />
  <main class="container">
    <router-view  :key="$route.path"></router-view>
    <ul>
    <li v-for="project in projects" :key="project.id">{{ project.title }}</li>
  </ul>

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
this.projects = res.data.results
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
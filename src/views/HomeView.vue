<!-- eslint-disable -->
<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">
        <SingleProject :project="project" @delete="handleDelete" @complete="handleComplete" />
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
import SingleProject from "../components/SingleProject.vue";
export default {
  name: "HomeView",
  components: {
    SingleProject,
  },
  data() {
    return {
      projects: [],
    };
  },
  methods: {
    handleDelete(id) {
      this.projects = this.projects.filter(project => {
        return project.id !== id
      })
    },
    handleComplete(id) {
      const p = this.projects.find(project => {
        return project.id === id
      })
      p.complete = !p.complete
    }
  },
  mounted() {
    fetch("http://localhost:3000/projects")
      .then((res) => res.json())
      .then((data) => (this.projects = data))
      .catch((error) => console.log(error.message));
  },
};
</script>

<!-- eslint-disable -->
<template>
  <div class="home">
    <FilterNave @filterChange="current = $event" :current="current" />
    <div v-if="projects.length">
      <div v-for="project in filteredProjects" :key="project.id">
        <SingleProject :project="project" @delete="handleDelete" @complete="handleComplete" />
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
import SingleProject from "../components/SingleProject.vue";
import FilterNave from "../components/FilterNav.vue";
export default {
  name: "HomeView",
  components: {
    SingleProject,
    FilterNave
  },
  data() {
    return {
      projects: [],
      current: 'all'
    };
  },
  computed: {
    filteredProjects() {
      if (this.current === 'completed') {
        return this.projects.filter(project => project.complete)
      }
      if (this.current === 'ongoing') {
        return this.projects.filter(project => !project.complete)
      }
      return this.projects
    }
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

<template>
  <div class="project">
    <div class="actions" @click="details.show = !details.show">
      <h3>{{ project.title }}</h3>
    </div>
    <div class="details" v-if="details.show">
      <p>{{ project.details }}</p>
    </div>
  </div>
</template>
<script>
/* eslint-disable */
export default {
  props: ["project"],
  data() {
    return {
      details: {
        show: false
      }
    }
  }
};
</script>
<style>
.project {
  margin: 20px auto;
  background: white;
  padding: 10px 20px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, .05);
  border-left: 4px solid #e90074;
}
</style>

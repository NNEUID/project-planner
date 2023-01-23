<template>
  <div class="project">
    <div class="actions" @click="details.show = !details.show">
      <h3>{{ project.title }}</h3>
      <div class="icons">
        <span class="material-icons">edit</span>
        <span class="material-icons">delete</span>
        <span class="material-icons">done</span>
      </div>
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

.actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.material-icons {
  font-size: 24px;
  margin-left: 10px;
  color: #bbb;
  cursor: pointer;
}

.material-icons:hover {
  color: #777;
}
</style>

<template>
  <div class="project" :class="{ complete: project.complete }">
    <div class="actions">
      <h3 @click="details.show = !details.show">{{ project.title }}</h3>
      <div class="icons">
        <span class="material-icons">edit</span>
        <span class="material-icons" @click="deleteProject">delete</span>
        <span class="material-icons tick" @click="toggleComplete">done</span>
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
        show: false,
      },
      uri: 'http://localhost:3000/projects/' + this.project.id
    }
  },
  methods: {
    deleteProject() {
      fetch(this.uri, { method: 'DELETE' })
        .then(() => this.$emit('delete', this.project.id))
        .catch(error => console.log(error))
    },
    toggleComplete() {
      fetch(this.uri, {
        method: 'PATCH',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ complete: !this.project.complete })
      }).then(() => this.$emit('complete', this.project.id)).catch(error => console.log(error))
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

.project.complete {
  border-left: 4px solid #00ce89;
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

.project.complete .tick {
  color: #00ce89;
}
</style>

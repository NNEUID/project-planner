<!-- eslint-disable -->
<template>
  <form>
    <label>Title:</label>
    <input type="text" required v-model="title">
    <label>Details:</label>
    <textarea required v-model="details"></textarea>
    <button>Add Project</button>
  </form>
</template>

<script>
/* eslint-disable */
export default {
  data() {
    return {
      data() {
        return {
          title: '',
          details: ''
        }
      }
    }
  }
}
</script>

<style>

</style>

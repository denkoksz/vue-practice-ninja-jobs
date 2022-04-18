<template>
  <div v-if="job">
    <h1>Job Details Page</h1>
    <h2>{{ job.title }}</h2>
    <p>The job id is: {{ id }}</p>
    <p>{{ job.details }}</p>
  </div>
  <div v-else>
    <p>Loading job details...</p>
  </div>
</template>

<script>
export default {
  props: ['id'],
  // data() {
  //   return {
  //     id: this.$route.params.id
  //   }
  // }
  data() {
    return {
      job: null
    }
  },
  mounted() {
    fetch('http://localhost:3000/jobs/' + this.id )
        .then(response => response.json())
        .then(data => this.job = data)
        .catch(err => console.log(err.message))
  }
}
</script>

<style>

</style>
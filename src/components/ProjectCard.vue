<script>
import axios from 'axios'

export default {
  name: 'ProjectCard',
  data() {
    return {
      projects: []
    };
  },
  created() {
    axios
      .get('http://127.0.0.1:8000/api/projects')
      .then(response => {
        console.log(response.data)

        this.projects = response.data.results
      })
  }
};


</script>

<template>

<div class="container">
  <div class="card" v-for="project in projects">
    <h2>
      <p>Title:</p> {{ project.title }}
    </h2>
    <h3>
      <p>Description:</p> {{ project.description }}
    </h3>
    <h3>
      <p>Slug:</p> {{ project.slug }}
    </h3>
  </div>
</div>

</template>

<style scoped>

.container{
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  color: gray;
}

.card{
  width: 25%;
  margin: 20px;
  border: 1px solid orange;
}
</style>

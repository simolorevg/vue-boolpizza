<script>
import axios from 'axios';
import projectCard from './projectCard.vue';

export default{
  name: "pizzas",
  components: {
    projectCard,
  },
  data(){
    return{
      projects: []
    }
  },
  mounted() {
    this.getPizzas();
  },
  methods: {
    getPizzas(){
      axios.get('http://127.0.0.1:8000/api/pizzas').then(resp => {
        this.projects = resp.data.results;
      })
    }
  }

}
</script>

<template>
  <div class="container ">
  <div class="row row-cols-4 m-3">
        <div class="project col mb-3" v-for="project in projects" :key="project.id" style="cursor: pointer;" >
          <projectCard :myProject="project"/>
        </div>
  </div>
  </div>
</template>

<style lang="scss" scoped>

</style>

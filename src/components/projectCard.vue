<script >


export default {
  name: 'ProjectCard',
  props: {
    myProject: Object

  },
  data() {
    return {
      
    }
  },
  computed: {

    preview() {
      //massimo 100 caratteri per la descrizione, poi si aggiunge ...
      if (!this.myProject.content) {
        return 'Nessun contenuto'
      } else if (this.myProject.content.length > 100) {
        return this.myProject.content.substring(0, 99) + "...";
      } else {
        return this.myProject.content
      }
    },

    imgSrc() {
      // Se post image inizia con https://, ritorna post.image
      // Altrimenti ritorna ${store.apiBaseUrl}/storage/${post.image} 

      if (!this.myProject.media_path) {
        this.isThere = true;
      } else {
        return `${this.myApi}/storage/${this.myProject.media_path}`;
      }
    }
  },
  methods:{
    
  }

}
</script>

<template>
  <div class="card d-flex flex-column" >

    <img v-show="myProject.media_path" :src="imgSrc" :alt="myProject.title" />
    <h5 v-if="isThere" class="my-4 d-flex align-items-center"> IMMAGINE NON DISPONBILE</h5>


    <div class="card-body mt-3">
      <h6 class="my-2"><span>Titolo: </span> {{ myProject.nome }}</h6>
      <h6 class="my-2"><span>Prezzo: </span> {{ myProject.prezzo }}</h6>
      <ul style="list-style-type: none;">
        <li v-for="ingredient in myProject.ingredients">
            {{ingredient.name}}
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {

  background-color: rgb(10 10 10 / 75%);
  height: 550px;

  h5 {
    color: rgb(6, 113, 194);
  }

  img {
    max-width: 100%;
  }

  .card-body {
    flex: none;
    height: 500px;

    ul {
      color: aquamarine;

     
    }

    h6 {
      color: green;
    }

    p {
      color: orange;
      font-size: 1.3rem;

    }

    span {
      color: red;
      font-size: 1.3rem;
    }
  }
}
</style>
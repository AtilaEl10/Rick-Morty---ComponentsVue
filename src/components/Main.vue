<template>
  <main class="hello">
    <img src="../assets/title.png" class="img-fluid col-sm-6 col-8 mx-auto" alt="RICK & MORTY">    
    <hr class="text-success">
    <h2 class="fw-bold my-4 text-success">PERSONAJES</h2>
    <button class="btn btn-warning mb-4" @click="getData">Mostrar Personajes</button>
    <div class="container" v-if="personajes.length > 0">
      <div class="row">
          <!--Inicio Card-->
        <div class="col-md-2 col-4 my-3" v-for="(person, i) in personajes" :key="i">
          <div class="circle">
            <img class="cardimg card-img-top img-fluid" :src=person.image alt="Card image cap">
          </div>
          <div class="card-body">
            <h5 class="card-title text-warning fw-bold">{{ person.name }}</h5>
          </div>
        </div>
        <!--Fin Card-->
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Main",
  data() {
    return {
      personajes: [],
    }
  },
  methods: {
    // mounted() {
      // this.getData()
    // },
    async getData() {
      const url = "https://rickandmortyapi.com/api/character";
      try {
        const request = await fetch(url);
        const requestJSON = await request.json();

        this.personajes = requestJSON.results
      } catch (error) {
        console.log(`Error en la llamada de la API: ${error}`);
      }
    }

  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
 .cardimg {
    border-radius: 50%;
 }
 .card-title {
  font-size: 20px; 
}
</style>

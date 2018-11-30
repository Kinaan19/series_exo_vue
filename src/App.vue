<template>
  <div id="app">
    <h1 class="my-5">{{titre}}</h1>
    <div id="nav">
      <router-link to="/"><button class="btn btn-info mb-5 mx-3">Home</button></router-link>
      <router-link to="/exo01"><button class="btn btn-info mb-5 mx-3">Exo01</button></router-link>
      <router-link to="/exo02"><button class="btn btn-info mb-5 mx-3">Exo02</button></router-link>
      <router-link to="/exo03"><button class="btn btn-info mb-5 mx-3">Exo03</button></router-link>
      <router-link to="/exo04"><button class="btn btn-info mb-5 mx-3">Exo04</button></router-link>
      <router-link to="/exo05"><button class="btn btn-info mb-5 mx-3">Exo05</button></router-link>
      <router-link to="/exo06"><button class="btn btn-info mb-5 mx-3">Exo06</button></router-link>
      <router-link to="/exo06bis"><button class="btn btn-info mb-5 mx-3">Exo06bis</button></router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
    data(){
        return {
            titre: "Home"
        }
    },
    methods: {
        display: function(titre){
          this.titre = titre;
        }
    }
}
</script>

<style>
@import "../node_modules/bootstrap/dist/css/bootstrap.css";
@import "../node_modules/@fortawesome/fontawesome-free/css/all.css";

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #000;
  text-align: center;
  margin-top: 60px;
}

</style>

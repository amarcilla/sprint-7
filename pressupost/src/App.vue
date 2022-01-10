<template>
  <!-- el primer Productes, es el Prompt de Home.vue   -->
  <!-- el segon productes, és el corresponent a la data()  -->
  <!-- <Home v-bind:Productes="productes" />  -->

  <Home
    v-bind:Productes="productes"
    v-bind:total="total"
    v-on:suma="suma"
    v-on:resta="resta"
    v-on:multiplica="multiplica"
  />
</template>

<script>
import Home from "./components/Home";

export default {
  name: "App",
  components: {
    Home,
  },
  data() {
    return {
      productes: [
        {
          id: 1,
          product: "Crear pàgina web",
          preu: 500,
          num: 0,
          numPagines: 0,
          numIdiomes: 0,
        },
        {
          id: 2,
          product: "Consultoria SEO",
          preu: 300,
          num: 0,
          numPagines: 0,
          numIdiomes: 0,
        },
        {
          id: 3,
          product: "Campaña google Adds",
          preu: 200,
          num: 0,
          numPagines: 0,
          numIdiomes: 0,
        },
      ],
      //total:0
    };
  },
  computed: {
    total() {
      var TotalP=0;      
      this.productes.forEach(function (element) {        
        TotalP =TotalP + (element.preu * element.num) + element.numPagines +  element.numIdiomes;
      });      
      return TotalP;
    },
  },
  methods: {    
    suma(id) {
      var p = this.productes.find((c) => c.id == id);      
      p.num=1;
      //this.total = parseInt(this.total) + parseInt(p.preu);
    },
    resta(id) {            
      var p = this.productes.find((c) => c.id == id);
      p.num=0;
      //this.total = parseInt(this.total) - parseInt(p.preu);
    },
    multiplica(pag, idi) {
      //console.log(pag + " " + idi);
      this.productes[0].numPagines = pag;
      this.productes[0].numIdiomes = idi;
      //this.total =  parseInt(this.total) +  parseInt(this.productes[0].numPagines) *   parseInt(this.productes[0].preu);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

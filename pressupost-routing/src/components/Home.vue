<template>
  <section id="main">
    <div>
      Que quieres hacer?
      <div v-for="product in Productes" :Key="product.id">
        <!-- v-bind:product="product", si no es diuen igual em dona error... ha de ser el item i el prompt del Listproductes amb el mateix nom   -->
        <!-- el primer es el item, el segon es el propmt  -->
        <ListProductes
          v-bind:product="product"
          v-on:suma="$emit('suma', product.id)"
          v-on:resta="$emit('resta', product.id)"
        />
      </div>
      <hr />

      <!-- CREAR PRESSUPOST  -->
      <div id="dadesForm">
        <form >
          <div class="form-row">Informació del pressupost:</div>
          <div class="form-row">
            Nom Pressupost: <input type="text" v-model="nomPressupost" />
          </div>
          <div class="form-row">
            Nom cliente: <input type="text" v-model="nomclient" />
          </div>
          <div class="form-row">Preu total del pressupost: {{ total }} €</div>
          <div class="form-row">
            <button v-on:click="enviaPressupost()">Envia Pressuspost</button>
          </div>
        </form>
      </div>
    </div>

    <div id="pressupost">
      <PressupostList v-bind:pressupost="pressupost" />
    </div>
  </section>
</template>


<script>
import ListProductes from "./ListProductes";
import PressupostList from "./PressupostList";
import axios from "axios";

export default {
  name: "Home",
  components: {
    ListProductes,
    PressupostList,
  },
  props: ["Productes", "total"],
  data() {
    return {
      pressupost: [],      
    };
  },
  methods: {
    enviaPressupost(){      
      let pressupostNew = {
            id: 7,
            nomPressupost: "Crear pàgina web 4",
            nomClient: "Cliente d",
            Servei: "Pressupost d",
            total: 4000
      };

      axios.post("http://localhost:3000/pressupost", pressupostNew ).then((result) => {
          console.log(result);     
       });
  }
  },

  /* Llegim JSON Amb AXIOS */
  async created(){
      const response  = await axios.get('http://localhost:3000/pressupost');
      this.pressupost = response.data;
  }
  
  /* Llegim JSON Amb fetch
   mounted(){
      fetch('http://localhost:3000/pressupost')
        .then((res)=> res.json() )
        .then(data => this.pressupost = data)
        .catch(err => console.log(err.message ))
     } 
  */

};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#main {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

#main > div {
  width: 49%;
}

#pressupost {
  margin: 0px, auto;
}

#dadesForm {
  display: inline-block;
  width: 85%;
  padding: 10px;
  border-radius: 10px;
  justify-content: center;
}

.form-row {
  display: flex;
  justify-content: left;
  padding: 0.5em;
}
</style>

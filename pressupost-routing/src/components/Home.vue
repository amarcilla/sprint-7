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
      <hr>
      <div id="dadesForm">
        <form>
          <div class="form-row">
            Informació del pressupost:
          </div>
          <div class="form-row">
            Nom Pressupost: <input type="text" v-model="nomPressupost" />
          </div>
          <div class="form-row">
            Nom cliente: <input type="text" v-model="nomclient" />
          </div>
          <div class="form-row">
            Preu total del pressupost: {{ total }} €
          </div>
          <div class="form-row">
            <button>Envia Pressuspost</button>
          </div>
        </form>
      </div>
    </div>

    <div id="pressupost">
      <PressupostList />
    </div>
  </section>
</template>


<script>
import ListProductes from "./ListProductes";
import PressupostList from "./PressupostList";

export default {
  name: "Home",
  components: {
    ListProductes,
    PressupostList,
  },
  methods: {},
  Data() {
    return {
      nomPressupost: this.nomPressupost,
      nomclient: this.nomClient,
    };
  },
  props: ["Productes", "total", "numPag"],
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

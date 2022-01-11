<template>
  <div>
    <div class="Products">
      <input type="checkbox" v-on:change="calcula($event)" />
      {{ product.product }}
      ( {{ product.preu }} €)
    </div>
    <!-- Mostrem únicament si el producte es crear una web -->
    <div class="panell">
      <Panell v-bind:product="product" v-if="product.id == 1 && ckeckedWeb" />
    </div>
  </div>
</template>

<script>
import Panell from "./Panell";

export default {
  name: "ListProductes",
  data() {
    return {
      //numPagines: this.numPagines
      ckeckedWeb: false,
    };
  },
  components: {
    Panell,
  },
  props: ["product"],
  events: {},
  methods: {
    //li passo el event per saber si el checkbox està seleccionat
    calcula(event) {
      if (event.target.checked == true ) {
        if (this.product.id == 1) this.ckeckedWeb = true; 
        console.log("entra");               
        this.$emit("suma", this.product.id);
      } else {
        this.ckeckedWeb = false;
        this.$emit("resta", this.product.id);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.panell {
  display: inline-block;
  width: 100%;
  list-style-type: none;
}
</style>
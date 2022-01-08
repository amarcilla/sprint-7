<template>
 <div >
    <p>
    <input type="checkbox" v-on:change= "calcula($event)">      
    {{ product.product }}
    ( {{ product.preu }} €)
    <!-- Mostrem únicament si el producte es crear una web -->
        <Panell v-bind:product="product"  v-if="product.id==1"   />               
    </p>    
  </div>      
</template>

<script>
import Panell from './Panell';

export default {
  name: "ListProductes",
   data() {
    return {
      //numPagines: this.numPagines
    };
  },
  components: {
    Panell,
  },
  props:['product'],   
  events:{

  },
  methods: {
      //li passo el event per saber si el checkbox està seleccionat
      calcula(event){            
        if (event.target.checked == true){        
          this.$emit('suma',this.product.id)        
        } else {
          this.$emit('resta',this.product.id)        
        }         
      }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
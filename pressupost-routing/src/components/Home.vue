<template>
  <div >
    Que quieres hacer?         
       <div v-for="product in Productes" :Key="product.id" >     
          <!-- v-bind:product="product", si no es diuen igual em dona error... ha de ser el item i el prompt del Listproductes amb el mateix nom   -->
          <!-- el primer es el item, el segon es el propmt  -->
          <ListProductes v-bind:product="product" v-on:suma="$emit('suma',product.id)" v-on:resta="$emit('resta',product.id)"   />  
       </div>
       Preu: Calcula total {{total}} €

       
  </div>
</template>

<script>
import ListProductes from './ListProductes';

export default {
  name: 'Home',
  components:{
    ListProductes,
  },
  methods: {
     
  },
  props:['Productes', 'total', 'numPag'] ,  
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

<template>
 <div >
    <p>
    <input type="checkbox" v-on:change= "calcula($event)">      
    {{ product.product }}
    ( {{ product.preu }} €)
    </p>    
  </div>      
</template>

<script>

export default {
  name: "ListProductes",
  props:['product'],   
  methods: {
      //li passe el event per saber si el checkbox està seleccionat
      calcula(event){            
        if (event.target.checked == true){        
          this.$emit('suma',this.product.id)        
        } else {
           alert("resta");
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
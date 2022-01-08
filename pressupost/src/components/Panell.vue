<template>
 <div >
    <form id='Panell'>
        Número de planes <input type="text"  v-on:change= "calculaPagines" v-model= "numPagines"  >
        Número d'idiomes <input type="text"  v-on:change= "calculaPagines" v-model= "numIdiomes" >        
     </form>
  </div>      
</template>

<script>

export default {
  name: "Panell",
  props:['product'],     
  data() {
    return {
      numPagines: this.product.numPagines,
      numIdiomes: this.product.numIdiomes,
    };
  },
  methods: {
      calculaPagines(){
          //console.log("pagines: " + this.numPagines + "  " + this.product.numPagines);
          //console.log("Idiomes: " + this.numIdiomes);          
          //parseInt(this.numPagines) + parseInt(this.numIdiomes)         
          this.$parent.$parent.$parent.$emit('multiplica', {numPagines: this.numPagines,  numIdiomes: this.numIdiomes} )
      }    
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  form{
     display: flex;
     flex-direction: column;
     align-items: center;
   }

  input[type="text"]{      
      flex-direction: column;
      padding: 5px;
      width: 100px;
      
  }

    input[type="submit"]{
      flex: 2;
  }

</style>
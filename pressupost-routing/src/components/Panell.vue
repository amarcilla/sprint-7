<template>
  <div>
    <form v-on:submit.prevent="submitForm">
       <transition name="fade">
            <div class="modal-overlay" v-if="showModal"> </div>
       </transition>

      <transition name="fade">
            <div class="modal" v-if="showModal">             
            <p >En aquest component has d'incloure el número de planes que tindrà el teu lloc web</p>
            <button @click="showModal = false" class="btn btn-primary"  > tancar </button>
            </div>
       </transition>

       <transition name="fade">
            <div class="modal-overlay" v-if="showModal2"> </div>
       </transition>

      <transition name="fade">
            <div class="modal" v-if="showModal2">             
            <p >En aquest component has d'incloure el número de planes que tindrà el teu lloc web</p>
            <button @click="showModal2 = false" class="btn btn-primary"  > tancar </button>
            </div>
       </transition>

      <ul class="wrapper">
        <li class="form-row">
          <label>Número de planes</label>
           <button v-on:click ="aumentarPag('pag')" class="boton" >+</button> 
          <input
            type="text"
            v-on:change="calculaPagines"
            v-model="numPagines"              
          />  
            <button v-on:click ="reducirPag('pag')"  class="boton" >-</button>
            <button  @click="showModal = true" class="btn btn-primary"  > i </button>
        </li>
        <li class="form-row">
          <label>Número d'idiomes </label>
          <button v-on:click ="aumentarIdi('idi')" class="boton" >+</button> 
          <input
            type="text"
            v-on:change="calculaPagines"
            v-model="numIdiomes"
          />
          <button v-on:click ="reducirIdi('idi')"  class="boton">-</button>
          <button  @click="showModal2 = true" class="btn btn-primary"> i </button>
        </li>
      </ul>
    </form>
    {{product.numPagines}}
    {{product.numIdiomes}}

    numP {{numPag}}
     
  
     

  </div>
</template>

<script>
export default {
  name: "Panell",
  props: ["product"],
  
  data() {
    return {
      numPagines: this.product.numPagines,
      numIdiomes: this.product.numIdiomes,
      showModal: false,
      showModal2: false,
    };
  },

  updated() {        
    this.numIdiomes= this.product.numIdiomes;
    this.numPagines= this.product.numPagines;
  },
  methods: {

    calculaPagines() {
      //console.log("pagines: " + this.numPagines + "  " + this.product.numPagines);
      //console.log("Idiomes: " + this.numIdiomes);
      //parseInt(this.numPagines) + parseInt(this.numIdiomes)
      //parent es per indicar a quin pare volem que vagi.. en aquest cas... anem a la Home .
      this.$parent.$parent.$emit(
        "multiplica",
        this.numPagines,
        this.numIdiomes
      );
    },
  
  reducirPag(){
      this.$parent.$parent.$emit("multiplica", this.numPagines-1, this.numIdiomes );
  },

   aumentarPag(){       
        this.$parent.$parent.$emit("multiplica", this.numPagines+1, this.numIdiomes );
  },

  reducirIdi(){
      this.$parent.$parent.$emit("multiplica", this.numPagines, this.numIdiomes-1);
  },

   aumentarIdi(){       
        this.$parent.$parent.$emit("multiplica", this.numPagines, this.numIdiomes+1 );
  },
  
  setvalue(){
    //this.numPagines= this.product.numPagines;
    console.log("this.numPagines-1");
  }

},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.wrapper {
  display:inline-block;
  border: solid;
  width: 85%;
  padding: 10px;
  border-radius: 10px;
  justify-content: center;  
}

.form-row {
  display: flex;
  justify-content: center;
  padding: 0.5em;
}

input[type="text"] {
  flex-direction: row;
  padding: 3px;
  width: 20px;
  border: 0ch;
}

input[type="submit"] {
  flex: 2;
}

.boton {
  font: inherit;
  cursor: pointer;
  border: 1px solid orange;
  background-color: orange;
  color: white;

  border-radius: 10px;
  margin: 0 1rem;
}

.boton:hover,
.boton:active {
  background-color: orange;
  border-color: orange;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

.modal{
  position: fixed;
  top: 25%;
  left: 25%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.4);
  z-index: 101;
}

.modal-overlay{
  position: absolute;
  top:  0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: 100;
  background: rgba(0, 0, 0, 0.4);
}

fade-enter{

}
</style>
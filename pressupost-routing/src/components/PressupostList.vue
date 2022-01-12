<template>
  <div>
    PRESSUPOSTOS
      <div v-for="pres in pressupost" :Key="pres.id">               
        {{pres.id}} -
        {{pres.nomPressupost}} -
        {{pres.nomClient}} -
        {{pres.Servei}} -
        {{pres.total}} € -
      </div>
  </div>
</template>


<script>
import axios from 'axios';

export default {
  name: "PressupostList",
  props: ["pressupost"],
  
};

</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
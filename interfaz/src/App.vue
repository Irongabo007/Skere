<template>
  <div class="container">
    <h1>Perritos</h1>
    <div class="mundos-container">
       {{ datu }}
    </div>
  </div>
</template>

<script>
import axios from "axios";
const API_URL = "https://dog.ceo/api/breeds/list/all";
export default {
  // la funcion de data nos permite guardar variables y objetos que luego pueden ser accedidos por el template
  data() {
  return {
        datu: []
      }
  },
  mounted(){
    axios.get('https://dog.ceo/api/breeds/list/all').then(respuesta=>this.datu=respuesta)
  },
  // la seccion de methods es donde creamos las funciones para esta vista o archivo
  methods: {
    obtenerDatitos() {
      axios
        .get(API_URL)
        .then((res) => {
          this.mundos = res.data;
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
  created() {
    this.obtenerDatitos()
  },
  
};

</script>

<style>

</style>
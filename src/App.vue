<template>
  <div id="app">
    <input type="text" v-model="nomedoFabio"> #utilizando two way binding 
    <input type="text" v-model="clienteFabio.nome"> #utilizando two way binding com o campo nome do objeto clienteFabio
    <Cliente2 /> #estatico, só com dados de "data"
    <Cliente2 nome="Petterson" email="peter@gmail.com" idade="50"/> #utilizando props + "data"  
    <Cliente2 :nome="nomedoFabio" email="fabio@gmail.com" idade="20"/> #utilizando props(com one way binding) + "data" 
    <Cliente2 :cliente="clienteFabio"/> #utilizando props(com one way binding do objeto clienteFabio) + "data" 
  </div>
</template>

<script>
import Cliente2 from './components/Cliente2.vue'

export default {
  name: 'App',
  data() {
    return {
      nomedoFabio: "Fábio Miranda Figueiredo",
      clienteFabio: {
        nome:"Fábio Miranda",
        email: "fabio@gmail.com",
        idade: 100
      }
    }
  },
  components: {
    Cliente2,
  }
}
</script>

<style>
</style>

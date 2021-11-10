<template>
  <!-- <div id="app">
    <input type="text" v-model="clienteFabio.nome">
    <input type="text" v-model="clienteFabio.email">
    <Cliente3 :cliente="clienteFabio" :showIdade="true"/>
    <Cliente3 :cliente="clienteFabio" :showIdade="true"/>
    <Cliente3 :cliente="clienteFabio" :showIdade="false"/>
    
    <div v-for="(cliente,index) in clientes" :key="cliente.id">
      <h1>{{ index }}</h1>
      <Cliente3 :cliente="cliente" :showIdade="true"/>
       <input type="text" v-model="cliente.nome">
       <input type="text" v-model="cliente.email">
    </div> 
  </div> -->

  <div id="app">

    <div class="buttons">
      <button class="button is-primary">Primary</button>
      <button class="button is-link">Link</button>
    </div>

    <h3>Cadastro: </h3>
    <small id="nomeError" v-show="deuErro">O nome é inválido, tente novamente!</small> <br> 
    <input type="text" placeholder="nome" v-model="nomeField"> <br>
    <input type="email" placeholder="email" v-model="emailField"> <br>
    <input type="number" placeholder="idade" v-model="idadeField"> <br>
    <button @click="cadastraCliente">Cadastrar novo cliente!</button>
    <hr>
    <div v-for="(cliente,index) in orderClientes" :key="cliente.id">
      <h1>{{ index }}</h1>
      <Cliente3 :cliente="cliente" :showIdade="true" @meDelete="deletarCliente($event)"/> 
    </div> 
  </div>
</template>

<script>
import Cliente3 from './components/Cliente3.vue'
import _ from 'lodash';

export default {
  name: 'App',
  data() {
    return {
      nomedoFabio: "Fábio Miranda Figueiredo",
      clienteFabio: {
        nome:"Fábio Miranda",
        email: "fabio@gmail.com",
        idade: 100
      },
      clientes: [
        {
          id: 0,
          nome:"Lucas",
          email:"lucas@gmail.com",
          idade:22
        },
        {
          id: 1,
          nome:"Filipe",
          email:"filipe@gmail.com",
          idade:22
        },
        {
          id: 2,
          nome:"João",
          email:"joao@gmail.com",
          idade:29
        },
      ],
      nomeField: "",
      emailField: "",
      idadeField: 0,
      deuErro: false,
    }
  },
  components: {
    Cliente3,
  },
  methods: {
    cadastraCliente: function() {
      if(this.nomeField == "" || this.nomeField == " " || this.nomeField.lenght < 3) {
        this.deuErro = true;
        console.log("Erro de Validação");
      }
      else {
        this.clientes.push({id: Date.now(), nome: this.nomeField, email:this.emailField, idade:this.idadeField})
        this.nomeField = "";
        this.emailField = "";
        this.idadeField = 0;
        this.deuErro = false;
      }
    },
    deletarCliente : function($event) {
      console.log("Recebendo evento!");
      // console.log($event);
      // $event.component.isPremium = !$event.component.isPremium;
      // console.log($event.idDoCliente)
      // $event.component.testar();
      var id = $event.idDoCliente;
      var novoArrayClientes = this.clientes.filter(cliente => cliente.id != id);
      this.clientes = novoArrayClientes;
    }
  },
  computed: {
    orderClientes () {
      return _.orderBy(this.clientes, ['nome'], ['asc']);
    }
  }
}
</script>

#Quando for mexer nos dados de um componente passado no this.$emit através do component: this, 
#alterar somente os dados que estão dentro da função data, não mexer nas props.

<style>
  #nomeError {
    color: red;
  }
</style>

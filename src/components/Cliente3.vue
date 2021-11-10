<template>
    <!-- #id é quando tem # la no style e class é quando tem . lá no style -->
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}"> 
        <h4>Nome: {{cliente.nome}} </h4>
        <hr>
        <p>Email: {{processarEmail}}</p>
        <p v-if="showIdade === true">Idade: {{cliente.idade}}</p>
        <p v-else>O usuário escondeu a idade</p> 
        <!-- existe também o v-else-if, em que diferentemente do v-else, também adiciona uma condição igual ao v-if -->
        <p v-show="showIdade === true">Idade: {{cliente.idade}}</p>
        <button @mouseenter="mudaCor($event)">Mudar cor!</button> 
        <button @click="emitirEventoDelete">Deletar!</button> 
        <h4>ID Especial: {{idEspecial}}</h4>
    </div>
</template>

<script>
export default {
    data(){ 
        return {
            isPremium: true
        }
    },
    props: {
        cliente: Object,
        showIdade: Boolean,
    },
    methods: {
        mudaCor: function($event) {
            console.log($event)
            this.isPremium = !this.isPremium
        },
        emitirEventoDelete: function() {
            console.log("Emitindo do filho");
            // this.$emit("meDelete", {curso: "VueJs", ano:2021, component: this});
            this.$emit("meDelete", {component: this, idDoCliente: this.cliente.id});
        },
        testar: function() {
            console.log("Testando!");
            alert("Alert!")
        },
    },
    computed: {
        processarEmail() {
            return this.cliente.email.toUpperCase();
        },
        idEspecial() {
            return (this.cliente.email + this.cliente.nome + this.cliente.id).toUpperCase();
        }
    }
}
</script>

<style scoped>
    .cliente {
        background-color: #ECE5E3;
        max-width: 600px;
        height: 250px;
        padding: 1%;
        margin-top: 2%;
    }

    .cliente-premium {
        background-color:black;
        color: yellow;
        max-width: 600px;
        height: 250px;
        padding: 1%;
        margin-top: 2%;
    }
</style>
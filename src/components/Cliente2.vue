<template>
    <div id="cliente">
        <h4>Nome: {{nome}} </h4>
        <hr>
        <p>{{descrição}}</p>
        <hr>
        <p>Número: {{numero}}</p>
        <p>Email: {{email}}</p>
        <p>Idade: {{idade}}</p>
    </div>
</template>

#props utilizado quando quero passar dados de um componente para outro componente,
#de um componente filho para um componente pai.

<script>
export default {
    data(){ 
        return {
            numero: "123456789",
            descrição: "Lorem ipsum"
        }
    },
    props: {
        nome: String,
        email: String,
        idade: Number,
        cliente: Object,
    }
}
</script>

<style scoped>
    #cliente {
        background-color: #ECE5E3;
        max-width: 600px;
        height: 250px;
        padding: 1%;
        margin-top: 2%;
    }
</style>
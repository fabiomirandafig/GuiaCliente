<template>
    <div id="cliente">
        <!-- One way data binding(é os dois pontos de :value, utilizado somente para leitura, não modifica dados): para quando quero utilizar 
        uma variável dentro de um atributo html(principalmente formulários).
        Ligando um dado em um campo de formulário. Ela é de um caminho pq se eu alterar o valor da variavel
        dentro do formulário, a mudança não reflete na mesma variavel que está sendo utilizada em outro lugar do html. -->
        <input type="text" :value="nome">
        <hr>
        <!-- Two way data bindings: permite modificar variaveis e que tais mudanças sejam replicadas em outras partes do html.
        Não funciona em todos tipos de atributos, funciona mais em formulários, checkbox, select.-->
        <input type="text" v-model="descrição">
        <!-- abaixo: aplicando reatividade através da interpolação para que dados que foram definidos no javascript possam ser utilizados dentro do html -->
        <h2 id="cliente-nome">{{nome}}</h2> 
        <p>Descrição do cliente: {{descrição}}</p>
    </div>
</template>


<script>
export default {
    // dados declarados dentro de "data" são dados reativos
    data(){ 
        return {
            nome: "Fábio Miranda",
            número: "123456789",
            email: "fabio@gmail.com",
            idade: 0,
            descrição: "Lorem ipsum"
        }
    }
}
</script>

<style scoped>
    #cliente {
        max-width: 600px;
        height: 120px;
    }
</style>
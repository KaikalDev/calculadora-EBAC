<script setup>
import { reactive } from 'vue';
import Formulario from './components/Formulario.vue';


const estado = reactive({
  numero1: '0',
  numero2: '0',
  operacao: '+',
  resposta: 0,
})

const executaOperacao = () => {
  switch (estado.operacao) {
    case '+':
      estado.resposta = parseInt(estado.numero1) + parseInt(estado.numero2);
      break;
    case '-':
      estado.resposta = parseInt(estado.numero1) - parseInt(estado.numero2);
      break;
    case '*':
      estado.resposta = parseInt(estado.numero1) * parseInt(estado.numero2);
      break;
    case '/':
      estado.resposta = parseInt(estado.numero1) / parseInt(estado.numero2);
      break;
  }
}

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Calculadora EBAC</h1>
      <p>
        Insira os numeros e a operação desejada
      </p>
    </header>
    <Formulario 
      :executa-operacao="executaOperacao"
      :get-numero1="evento => estado.numero1 = evento.target.value"
      :get-numero2="evento => estado.numero2 = evento.target.value"
      :get-operacao="evento => estado.operacao = evento.target.value"
      :retorna-resposta="estado.resposta"
    />
  </div>
</template>

<style scoped>
.resultado {
  height: 100%;
  border-radius: 10px;
  text-align: center;
}
</style>

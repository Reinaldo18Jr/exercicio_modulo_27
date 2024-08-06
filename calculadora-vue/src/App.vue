<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    filtro: "adicao",
    numero1: 0,
    numero2: 0,
  });

  const adicao = ({numero1, numero2} = estado) => {
    return numero1 + numero2;
  };

  const subtracao = ({numero1, numero2} = estado) => {
    return numero1 - numero2;
  };

  const multiplicacao = ({numero1, numero2} = estado) => {
    return numero1 * numero2;
  };

  const divisao = ({numero1, numero2} = estado) => {
    return numero1 / numero2;
  };

  const calculadora = () => {
    const {numero1, numero2, filtro} = estado;

    if((numero1, numero2)) {
      switch (filtro) {

        case "adicao":
          return adicao();

        case "subtracao":
          return subtracao();

        case "multiplicacao":
          return multiplicacao();

        case "divisao":
          return divisao();
      }
    }
  }
</script>

<template>
  <div class="container">
    <header class="mb-5 mt-5">
      <h1>Calculadora Vue.js</h1>
    </header>
    <body>
      <form>
        <div class="row">
          <div class="col-md-2 mb-4">
            <select @change="evento => estado.filtro = evento.target.value" class="form-control">
              <option value="adicao">ADIÇÃO ( + )</option>
              <option value="subtracao">SUBTRAÇÃO ( - )</option>
              <option value="multiplicacao">MULTIPLICAÇÃO ( * )</option>
              <option value="divisao">DIVISÃO ( / )</option>
            </select>
          </div>
        </div>
        <div class="row">
          <div class="col-md-3">
            <input @keyup="evento => estado.numero1 = Number(evento.target.value)" required type="number" class="form-control">
          </div>
          <div class="col-md-3">
            <input @keyup="evento => estado.numero2 = Number(evento.target.value)" required type="number" class="form-control">
          </div>
          <div class="col-md-3">
            <span>{{ calculadora() }}</span>
          </div>
        </div>
      </form>
    </body>
  </div>
</template>

<style scoped>
</style>

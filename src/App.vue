<script setup>
  import {reactive} from 'vue';

  const numbers = reactive({
    filtrando: 'calc',
    nOne: 0,
    nTwo: 0,
  })

  function calc() {
    const {nOne, nTwo} = numbers;
    return Number(nOne) + Number(nTwo)
  }
  function subtrair() {
    const {nOne, nTwo} = numbers;
    return Number(nOne) - Number(nTwo)
  }
  function multiplicar() {
    const {nOne, nTwo} = numbers;
    return Number(nOne) * Number(nTwo)
  }
  function dividir() {
    const {nOne, nTwo} = numbers;
    if (nOne && nTwo > 0) {
      return nOne / nTwo
    }else {
      return 0
    }
  }
  const resultado = () => {
    const {filtrando} = numbers;
    switch (filtrando) {
      case 'subtrair':
        return subtrair();
      case 'multiplicar':
        return multiplicar();
      case 'dividir':
        return dividir()
      default:
        return calc()
    }
  }
</script>

<template>
  <div class="cont">
    <header class="header">
      <h1 class="header_title">
        Calculando no VUEJS
      </h1>
    </header>
    <section class="calculadora">
    
      <input class="calc_inp" type="number" placeholder="Primeiro numero" @keyup="evento => numbers.nOne = evento.target.value">
      <select class="calculadora_select" @change="evento => numbers.filtrando = evento.target.value">
        <option value="calc">Somando</option>
        <option value="subtrair">Subtraindo</option>
        <option value="multiplicar">Multiplicando</option>
        <option value="dividir">Dividindo</option>
      </select>
      <input class="calc_inp" type="number" placeholder="Segundo numero" @keyup="evento => numbers.nTwo = evento.target.value">
      <span class="send_calc">
        {{ resultado() }}
      </span>
    </section>
  </div>
</template>



<style scoped>


 * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  
 }

.cont {
display: flex;
flex-direction: column;
position: relative;
top: 120px;
  margin: 0 auto;
  max-width: 820px;
  border-radius: 12px;
  background-color: black;
  font-family: sans-serif;

 }

 .header {

  margin-top: 50px;
  margin-bottom: 24px;
  text-align: center;
  padding: 22px 0;
  
 }

 .header_title {
  user-select: none;
   color: white;
  font-size: 36px;

 }

 .calculadora {

  display: flex;
  justify-content: center;
  align-items: center;
  padding-bottom: 24px;
  
 }

 .calc_inp {
  margin: 0px 16px;
    background-color: white;
  padding: 8px;
  border: none;
  outline: none;
  font-size: 16px;
  border-radius: 8px;
 }

 .calc_inp::-webkit-inner-spin-button {
  -webkit-appearance: none;
 }

 .calculadora_select {
  font-size: 22px;
  font-weight: bold;
  background-color: white;
  height: 30px;
  border-radius: 8px;
  border: none;
  outline: none;

 }

 .send_calc {
  display: flex;
  flex-direction: column;
  font-size: 20px;
  color: #f3f3f3;
 }
</style>

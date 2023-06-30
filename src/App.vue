<script setup>


import { ref, computed } from "vue";

let arrayNumeros = ref([]);

let contador = ref(0);
const aumentar = () => {
  contador.value ++;
  
}
const disminuir = () => {
  contador.value --;
  
}

const reset = () => {
  contador.value = 0;
  
}

const agregar = () => {
  arrayNumeros.value.push(contador.value);
  console.log(arrayNumeros);
}

const classCounter = computed(() => {
  if (contador.value > 0){
    return 'positivo';
  } else if (contador.value < 0) {
    return 'negativo';
  } else {
    return 'zero';
  }

})


 const validacion = computed(() => {
  const comparado = arrayNumeros.value.find(num => num === contador.value);
  console.log(comparado);
  if (comparado !== undefined) {
    return true;
  }
  return false;
 });
</script>


<template>
  <h1 :class="classCounter"> {{ contador }}</h1>
  <button @click="aumentar">Aumentar</button>
  <button @click="disminuir">Disminuir</button>
  <button @click="reset">Reset</button>
  <button @click="agregar" :disabled="validacion" >Agregar</button>
{{ arrayNumeros }}
  <ul>
    <li v-for="(num, index) in arrayNumeros" :key="index">
       {{ num }}
    </li>

  </ul>
 
</template>

<style>


.positivo {
  color:blue;
}
.negativo {

  color:red;
}
.zero {
  color: black;
}


</style>
<script setup>
import { ref } from "vue"; // importa la funcion 'ref', se utiliza para crear una referencia reactiva (variable reactiva en Vue)
const counter = ref(0); // para que empiece en 0
const increment = () => counter.value++; // Se puede poner lo de function()=>{...}
</script>

<template>
    <button @click="increment">Counter {{ counter }}</button>
</template>
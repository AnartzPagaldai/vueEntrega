<script setup>
import { ref } from "vue"

const id = ref();
const nombre = ref();
const fecha = ref();
const emit = defineEmits(["insertar"]);
</script>

<template>
    <label for="id">Id:</label>
    <input type="text" id="id" v-model="id">
    <label for="nombre">Nombre:</label>
    <input type="text" id="nombre" v-model="nombre">
    <label for="fecha">Fecha de nacimiento:</label>
    <input type="text" id="fecha" v-model="fecha">
    <button @click="() => emit('insertar', id, nombre, fecha)">insertar</button>
</template>

<style scoped>
</style>
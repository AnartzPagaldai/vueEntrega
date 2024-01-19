<script setup>
import {reactive, watch, provide } from "vue";
import alumno from "./components/alumno.vue";
import insertar from "./components/insertar.vue";
const alumnos = reactive(JSON.parse(localStorage.getItem("alumnos")) ?? []);

provide("alumnos", alumnos);

watch(alumnos, () => {
    console.log(alumnos);
})

function fnInsertar(id, nombre, fecha) {
    alumnos.push({id: id, nombre: nombre, fecha: fecha});
}

function borrar(alumno) {
    alumnos.splice(alumnos.indexOf(alumno), 1);
}

window.addEventListener("beforeunload", () => {
    localStorage.setItem("alumnos", (JSON.stringify(alumnos)))
})
</script>

<template>
    <div class="container">
        <insertar @insertar="fnInsertar"/>
        <alumno v-for="alumno of alumnos" :alumno="alumno" @borrar="borrar"/>
    </div>
</template>

<style scoped>
    .container {
        display: flex;
        flex-direction: column;
    } 
</style>

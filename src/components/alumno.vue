<script setup>
import { onBeforeUnmount, ref } from "vue";
const props = defineProps(["alumno"]);
const show = ref(false);
const emit = defineEmits(["borrar"]);

function changeShow() {
    show.value = !show.value;
}

onBeforeUnmount(() => {
    show.value = false;
})

</script>

<template>
    <div>
        <h1 @click="changeShow">{{ alumno.nombre }}</h1>
        <button @click="() => emit('borrar', alumno)">borrar</button>
    </div>
    <div v-if="show">
        <p>id:</p>
        <input type="text" v-model="alumno.id">
        <p>nombre:</p>
        <input type="text" v-model="alumno.nombre">
        <p>fecha:</p>
        <input type="text" v-model="alumno.fecha">
    </div>
    <br>
</template>

<style scoped>
    h1 {
        border: 1px solid rgb(101, 61, 137);
        display: inline;
    }
</style>
<script setup>
// import { onMounted } from 'vue';

defineProps({
    title: String,
    id: Number,
    body: {
        type: String,
        default: "Sin descripcion",
    },
    colorText: String,
});

// const posts = ref([]);

// onMounted(async () => {
//     try {
//         const response = await fetch('https://jsonplaceholder.typicode.com/posts');
//         postData.value = await response.json();
//     } catch (error) {
//         console.log('Error en el fecth: ', error);
//     }
// })

// Para emitir un evento tiene que estar anidado
const emit = defineEmits(['cambiarFavoritoNombre']);
</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title" :class="`text-${colorText}`">{{ id }} - {{ title }}</h5>
            <p>{{ body }}</p>
            <!-- $emit es una libreria -->
            <!-- <button @click="$emit('cambiarFavoritoNombre', title)" class="btn btn-outline-primary">
                Favorito
            </button> -->
            <button @click="emit('cambiarFavoritoNombre', title)" class="btn btn-outline-primary">
                Favorito
            </button>
        </div>
    </div>
</template>
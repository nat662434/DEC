<script setup>
import { ref } from "vue";

const newArtikulo = ref('');
const artikuloak = ref([]);
const erostekoLista = ref([]);
const erositakoLista = ref([]);

const actualizarValores = (articulos, index) => {
    if (articulos.value[index].completed) {
        erostekoLista.value.splice(articulos.value[index])
        erositakoLista.value.push(articulos.value[index]);
    } else {
        erositakoLista.value.splice(articulos.value[index])
        erostekoLista.value.push(articulos.value[index]);
    }
}

const addTask = () => {
    if (newArtikulo.value.length < 1) return alert("Artikuloaren izena ezin da hutzik egon");
    artikuloak.value.push({ title: newArtikulo.value, kantitatea: 1, completed: false });

    const index = artikuloak.value.length - 1; // Obtener el índice del último elemento añadido
    actualizarValores(artikuloak, index)

    newArtikulo.value = '';
}

const gehitu = (index) => {
    artikuloak.value[index].kantitatea++;
}

const kendu = (index) => {
    artikuloak.value[index].kantitatea--;
}
const cambioEstado = (index) => {
    artikuloak.value[index].completed = !artikuloak.value[index].completed;
    actualizarValores(artikuloak, index)
}

</script>
<template>
    <div>
        <h1>Erosketa lista</h1>

        <input v-on:keyup.enter="addTask" v-model="newArtikulo" type="text" class="form-control">
        <button type="submit" @click="addTask" class="btn btn-primary">Gehitu artikuloa</button>

        <hr>
        <h3>Erosteko</h3>
        <ul v-for="(artikulo, index) in erostekoLista">
            <li :key="index" @click="cambioEstado(index)" v-if="artikulo.completed == false">
                {{ artikulo.title }} -> Kantitatea: {{ artikulo.kantitatea }} {{ artikulo.completed }}
            </li>
            <i @click="gehitu(index)">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                        class="bi bi-plus-square" viewBox="0 0 16 16">
                        <path
                            d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2z" />
                        <path
                            d="M8 4a.5.5 0 0 1 .5.5v3h3a.5.5 0 0 1 0 1h-3v3a.5.5 0 0 1-1 0v-3h-3a.5.5 0 0 1 0-1h3v-3A.5.5 0 0 1 8 4" />
                    </svg>
                </i>
                <i @click="kendu(index)">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                        class="bi bi-dash-square" viewBox="0 0 16 16">
                        <path
                            d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2z" />
                        <path d="M4 8a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 0 1h-7A.5.5 0 0 1 4 8" />
                    </svg>
                </i>
        </ul>

        <hr>
        <h3>Erosita</h3>
        <ul v-for="(artikulo, index) in erositakoLista">
            <li :key="index" @click="cambioEstado(index)" v-if="artikulo.completed == true">
                {{ artikulo.title }} -> Kantitatea: {{ artikulo.kantitatea }}
                <i @click="gehitu(index)">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                        class="bi bi-plus-square" viewBox="0 0 16 16">
                        <path
                            d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2z" />
                        <path
                            d="M8 4a.5.5 0 0 1 .5.5v3h3a.5.5 0 0 1 0 1h-3v3a.5.5 0 0 1-1 0v-3h-3a.5.5 0 0 1 0-1h3v-3A.5.5 0 0 1 8 4" />
                    </svg>
                </i>
                <i @click="kendu(index)">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                        class="bi bi-dash-square" viewBox="0 0 16 16">
                        <path
                            d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2z" />
                        <path d="M4 8a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 0 1h-7A.5.5 0 0 1 4 8" />
                    </svg>
                </i>
            </li>
        </ul>

    </div>
</template>

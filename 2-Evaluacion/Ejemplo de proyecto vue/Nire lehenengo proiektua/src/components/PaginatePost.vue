<script setup>
defineProps(["inicio", "fin", "maxLength"]);
const emit = defineEmits(["next", "prev"]);
</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button @click="emit('prev')" type="button" class="btn btn-primary" :disbled="inicio === 0">
            Previous
        </button>
        <button @click="emit('next')" type="button" class="btn btn-primary" :disabled="fin >= maxLength">
            Next
        </button>
        <!-- <button type="button" class="btn btn-primary">Right</button> -->
    </div>
</template>

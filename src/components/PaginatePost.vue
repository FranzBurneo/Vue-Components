<script setup>
    defineProps(['inicio', 'fin', 'maxLength']);
    const emit = defineEmits(['next', 'previus']);

    const activarSiguiente = () => {
        console.log("me diste siguiente");
        emit("next");
    }
</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
    <button type="button" class="btn btn-outline-primary"
    @click="emit('previus')"
    :disabled="inicio<=0"
    >
    Previus
    </button>    
    <button type="button" class="btn btn-outline-primary"
    @click="activarSiguiente"
    :disabled="fin>=maxLength"
    >
    Next
    </button>
    </div>
</template>
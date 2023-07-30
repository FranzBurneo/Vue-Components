<script setup>
    // defineProps(["id", "title", "body"])
    defineProps({
        title: String,
        id: Number,
        body: {
            type: String,
            default: "No description"
        },
        cambiarFavorito: Function,
    });

    // const emit = defineEmits(['cambiarFavoritoNombre'])
</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title"
            >
                {{id}} - {{title}}
            </h5>
            <p>
                {{ body }}
            </p>
            <button 
            @click="cambiarFavorito(title)"
            class="btn btn-outline-primary"
            >
                Favorite
            </button>
        </div>
    </div>
</template>
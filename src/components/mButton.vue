<script setup>

const props = defineProps({
    texto: String
})

</script>

<template>

    <button type="button"> 
            <slot> 
                {{ props.texto }} 
            </slot>
        </button>
    
    
</template>

<style scoped>

</style>
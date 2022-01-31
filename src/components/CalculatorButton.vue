<template>
    <button
        class="calc-button"
        @click="$emit('clicked', val)">
            {{ val }}
        </button>
</template>

<script>
export default {
    props: {
        val: {
            type: [Number, String],
            default: " "
        },
    }
}
</script>

<style>
    
</style>
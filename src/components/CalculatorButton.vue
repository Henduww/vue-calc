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
    .calc-button {
        padding: 5px;
        background-color: #676767;
        color: white;
        border: 1px solid #939393;
        border-radius: 5px;
    }

    .equals {
        background-color: #FF7300;
    }
</style>
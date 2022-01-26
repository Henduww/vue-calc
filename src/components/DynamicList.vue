<template>
    <ul :class="$attrs.class">
        <li v-for="(item, i) in list" :key="i">
            {{ item }}
        </li>
    </ul>
</template>

<script>
export default {
    props: {
        list: {
            type: Array,
            required: true
        }
    }
}
</script>

<style>

</style>
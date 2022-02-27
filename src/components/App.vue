<template>
    <desktop></desktop>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Desktop from './desktop/Index.vue'

const App = defineComponent({
    components: {
        Desktop
    }
})

export default App
</script>

<style>
*,
*::before,
*::after {
    box-sizing: border-box;
}

html {
    font-size: 16px;
    font-family: sans-serif;
}

body {
    font-family: "Poppins", "Sarabun", Arial, Helvetica, sans-serif;
    font-size: 1rem;
    font-weight: 400;
    color: rgb(37, 37, 37);
    line-height: 1.25;
    margin: 0;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    /* user-select: none; */
}

h1, h2, p {
    margin-top: 0;
    margin-bottom: 1rem;
}
</style>
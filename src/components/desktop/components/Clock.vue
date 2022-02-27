<template>
    <span>{{ clockText }}</span>
</template>

<script lang="ts">
    import { defineComponent } from 'vue'

    const Clock = defineComponent({
        data() {
            return {
                clockText: '--:--',
                timeId: 0
            }
        },
        mounted() {
            this.timeId = setInterval(() => {
                const date = new Date()
                this.clockText = `${date.getHours()}:${date.getMinutes()}`
            }, 1000)
        },
        unmounted() {
            clearInterval(this.timeId)
        }
    })

    export default Clock
</script>
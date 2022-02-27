<template>
    <svg viewBox="0 0 250 250" xmlns="http://www.w3.org/2000/svg" :onmouseover="startAnimate">
        <circle
            cx="125"
            cy="125"
            r="100"
            fill="none"
            :stroke="color"
            stroke-width="14"
            :stroke-dasharray="`${lineWidth} ${maxLine}`"
        />
    </svg>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    props: {
        per: {
            type: Number,
            default: 0
        },
        color: {
            type: String,
            default: '#000'
        }
    },
    data() {
        return {
            lineWidth: 0,
            maxLine: 2 * Math.PI * 100,
            state: false
        }
    },
    mounted() {
        this.startAnimate()
    },
    methods: {
        sleep(time: number): Promise<void> {
            return new Promise(resolve => setTimeout(resolve, time))
        },
        async startAnimate() {
            if (!this.state) {

                this.lineWidth = 0
                this.state = true

                for (let i = 0; i <= this.per; i++) {
                    this.lineWidth = (i * this.maxLine) / 100
                    await this.sleep(10)
                }

                this.state = false
            }
        }
    }
})
</script>
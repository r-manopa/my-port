<template>
    <div class="title-bar">
        <star-icon class="app-icon"></star-icon>
        <h1>{{ barTitle }}</h1>
        <div class="grow"></div>
        <clock class="clock"></clock>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import StarIcon from '@/components/icon/Star.vue'
import Clock from './Clock.vue'

export default defineComponent({
    props: {
        barTitle: String
    },
    components: {
        StarIcon,
        Clock
    }
})

</script>

<style scoped>
.title-bar {
    /* position: absolute;
        top: 0;
        left: 0;
        right: 0; */
    height: 2rem;
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 0 1rem;
    z-index: 999999;
    color: #fff;
    background-color: rgba(255, 255, 255, 0.3);
    box-shadow: 0 0 2rem rgba(36, 36, 36, 0.5);
    /* backdrop-filter: blur(1rem); */
}

.grow {
    flex-grow: 1;
}

.title-bar h1 {
    margin: 0;
    font-size: 1rem;
    font-weight: 600;
    text-shadow: 0 0 0.5rem rgba(105, 105, 105, 0.514);
}

.title-bar .app-icon {
    width: 1.2rem;
    height: 1.2rem;
    margin-right: 1rem;
}
</style>
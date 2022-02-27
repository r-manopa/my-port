<template>
    <div class="icon-container">
        <word-icon></word-icon>
        <p>Profile</p>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import WordIcon from '@/components/icon/Word.vue'

export default defineComponent({
    components: {
        WordIcon
    }
})
</script>

<style scoped>
.icon-container {
    color: #fff;
    width: 48px;
    border: 1px solid transparent;
    border-radius: 6px;
}
.icon-container:hover {
    border-color: rgba(255, 255, 255, 0.4);
}
.icon-container p {
    font-size: 0.8rem;
    font-weight: 600;
    text-align: center;
    margin: 0;
    text-shadow: 0 0 2rem rgba(0, 0, 0, 0.5);
}
</style>
<template>
    <div class="root">
        <title-bar :bar-title="appTitle"></title-bar>
        <div class="content">
            <file-icon :ondblclick="onOpenFile"></file-icon>
            <app-wrapper app-title="Ronnachai Manopa Profile" :close="onAppClose" v-if="openFile">
                <profile></profile>
            </app-wrapper>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TitleBar from './components/TitleBar.vue'
import AppWrapper from './components/AppWrapper.vue'
import Profile from '../Profile.vue'
import FileIcon from './components/FileIcon.vue'

const Desktop = defineComponent({
    data() {
        return {
            openFile: true,
            appTitle: "Ronnachai Manopa Profile"
        }
    },
    methods: {
        onAppClose() {
            this.openFile = false
        },
        onOpenFile() {
            this.openFile = true
        }
    },
    watch: {
        openFile(value: boolean) {
            console.log()
            this.appTitle = value ? 'Ronnachai Manopa Profile' : 'KK OS'
        }
    },
    components: {
        TitleBar,
        AppWrapper,
        Profile,
        FileIcon
    }
})

export default Desktop

</script>

<style scoped>
.root {
    position: relative;
    height: 100vh;
    background-image: url(@/images/bg.jpeg);
    background-size: cover;
    background-attachment: fixed;
    background-position: center center;
    overflow: hidden;
}
.content {
    padding: 1rem;
}
</style>
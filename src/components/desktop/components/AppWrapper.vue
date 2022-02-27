<template>
    <div ref="wrapper" class="app-wrapper">
        <div ref="wrapperTitle" class="app-wrapper-title">
            <div class="close" :onclick="close">
                <close-icon></close-icon>
            </div>
            <span>{{ appTitle }}</span>
        </div>
        <div class="app-wrapper-content">
            <slot></slot>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, type StyleValue } from 'vue'
import interact from 'interactjs'
import CloseIcon from '@/components/icon/Close.vue'

export default defineComponent({
    components: {
        CloseIcon
    },
    props: {
        appTitle: String,
        close: Function
    },
    data() {
        return {
            x: 0,
            y: 0
        }
    },
    mounted() {
        this.dragInit()
    },
    methods: {
        dragInit() {

            const self = this
            const w = self.$refs.wrapper as HTMLDivElement
            const wt = self.$refs.wrapperTitle as HTMLDivElement

            w.style.width = `${window.innerWidth / 2}px`
            w.style.height = `${window.innerHeight - 150}px`
            const initX = (window.innerWidth / 2) - (w.offsetWidth / 2)
            const initY = 30

            w.style.transform = `translate(${initX}px, ${initY}px)`

            self.x = initX
            self.y = initY

            interact(w)
                .resizable({
                    edges: { top: true, left: true, bottom: true, right: true },
                    listeners: {
                        move(e) {

                            const x = self.x + e.deltaRect.left
                            const y = self.y + e.deltaRect.top

                            if (x > 0 && y > 0 && (x + e.rect.width) < window.innerWidth && (y + e.rect.height) < window.innerHeight) {
                                const style: StyleValue = {
                                    width: `${e.rect.width}px`,
                                    height: `${e.rect.height}px`,
                                    transform: `translate(${x}px, ${y}px)`
                                }

                                Object.assign(e.target.style, style)
                                Object.assign(e.target.dataset, { x, y })

                                self.x = x
                                self.y = y

                            }
                        }
                    }
                })

            interact(wt)
                .draggable({
                    listeners: {
                        move(e) {
                            const x = self.x + e.dx
                            const y = self.y + e.dy

                            if (x > 0 && y > 0 && (x + w.offsetWidth) < window.innerWidth && (y + w.offsetHeight) < window.innerHeight) {

                                w.style.transform = `translate(${x}px, ${y}px)`

                                self.x = x
                                self.y = y
                            }

                        },
                    }
                })
        }
    }
})

</script>

<style scoped>
.app-wrapper {
    position: absolute;
    display: flex;
    flex-direction: column;
    /* width: 800px;
    height: 900px; */
    top: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
}

.app-wrapper-title {
    display: flex;
    flex-direction: row;
    align-items: center;
    flex-shrink: 0;
    color: #fff;
    font-size: 1rem;
    font-weight: 600;
    text-shadow: 0 0 0.5rem rgba(105, 105, 105, 0.514);
    padding-left: 1rem;
    padding-right: 1rem;
    height: 2rem;
    background-color: rgba(255, 255, 255, 0.3);
    /* backdrop-filter: blur(1rem); */
    border-top-left-radius: 0.5rem;
    border-top-right-radius: 0.5rem;
}

.app-wrapper-title .close {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 14px;
    height: 14px;
    margin-right: 1rem;
    border-radius: 50%;
    cursor: default;
    color: rgba(161, 0, 0, 0.911);
    background-color: rgb(255, 73, 73);
}
.app-wrapper-content {
    flex-grow: 1;
    background-color: #fff;
    border-bottom-left-radius: 0.5rem;
    border-bottom-right-radius: 0.5rem;
    overflow-y: auto;
}
</style>
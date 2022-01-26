<template>
    <mesh :rotation-y="rotY" :position-x="x" :position-y="y">
        <boxGeometry />
        <meshPhysicalMaterial :color="color" />
    </mesh>
</template>

<script lang="ts" setup>
import { onBeforeRender } from 'lunchboxjs'
import palettes from 'nice-color-palettes'
import { defineProps, ref } from 'vue'

const palette = palettes[43]
const color = palette[Math.floor(Math.random() * palette.length)]
const props = defineProps<{
    x: number
    y: number
    index: number
}>()

const x = ref(props.x)
const y = ref(props.y)
const rotY = ref(0)

onBeforeRender(() => {
    rotY.value = Math.sin(Date.now() * 0.001 * props.index) * 0.8
})
</script>
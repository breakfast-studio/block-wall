<template>
    <Lunchbox
        :background="'midnightblue'"
        :cameraPosition="[5, 3, 10]"
        :cameraLook="[0, 0.5, 0]"
        orthographic
        shadow
    >
        <ambientLight :intensity="0.7" />
        <pointLight castShadow :position="[-cols * 0.5, rows + 1, 5]" />

        <group v-for="y in rows" :key="y" :y="-rows * 0.5">
            <SingleBlock
                castShadow
                receiveShadow
                v-for="x in cols"
                :key="x"
                :x="x - cols * 0.5"
                :y="y"
                :index="(y * rows + x) * 0.05"
            />
        </group>
    </Lunchbox>
</template>

<script setup lang="ts">
import SingleBlock from './SingleBlock.vue'

const cols = 20
const rows = 10
</script>
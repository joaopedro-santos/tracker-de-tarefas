<template>
    <section>
        <strong>{{ tempoDecorrido }}</strong>
    </section>
</template>

<script setup lang="ts">
import { computed, defineProps } from 'vue'

const props = defineProps({
    tempoEmSegundo: {
        type: Number,
        default: 0
    }
})

const tempoDecorrido = computed(() : string => {
    return new Date(props.tempoEmSegundo * 1000).toISOString().substr(11, 8)
})
</script>

<style></style>
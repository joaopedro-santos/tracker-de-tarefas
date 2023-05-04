<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <Cronometro v-bind:tempoEmSegundo="tempoEmSegundo" />
        <button class="button" @click="iniciar()" v-bind:disabled="cronometroRodando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>

        <button class="button" @click="finalizar()" v-bind:disabled="!cronometroRodando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script setup lang="ts">
import { ref, defineEmits } from 'vue'
import Cronometro from '../components/Cronometro.vue'

const tempoEmSegundo = ref(0)
const cronometro = ref(0)
const cronometroRodando = ref(false)

const emit = defineEmits([
    'aoTemporizador'
])

const iniciar = () => {
    cronometroRodando.value = true
    cronometro.value = setInterval(() => {
        tempoEmSegundo.value += 1
    }, 1000)
}

const finalizar = () => {
    cronometroRodando.value = false
    clearInterval(cronometro.value)
    
    //Emit pode definir os eventos que um componente pode emitir para seu pai
    emit('aoTemporizador', tempoEmSegundo.value)
    tempoEmSegundo.value = 0
}
</script>

<style></style>
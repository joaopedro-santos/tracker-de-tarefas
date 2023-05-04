<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>

            <div class="column">
                <Temporizador @aoTemporizador="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, defineEmits } from 'vue'
import Temporizador from '../components/Temporizador.vue'

const emit = defineEmits([
    'aoSalvarTarefa'
])

const descricao = ref('')

const finalizarTarefa = (tempoDecorrido: number) :void  => {
    emit('aoSalvarTarefa', {
        duracaoEmSegundos: tempoDecorrido,
        descricao: descricao.value
    })
    descricao.value = ''    
}

</script>

<style></style>
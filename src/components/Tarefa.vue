<template>
    <div class="box has-texte-weight-bold">
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao }}
            </div>

            <div class="column is-7">
                <Cronometro :tempoEmSegundo="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { defineProps, PropType } from 'vue'
import Cronometro from '../components/Cronometro.vue'
import ITarefa from '../interface/ITarefa';

const props = defineProps({
    tarefa:{
        type: Object as PropType<ITarefa>,
        required: true
    }
})

</script>

<style scoped>
.box {
    background: #faf0ca;
}
</style>
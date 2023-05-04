<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
      
    </div>

    <div class="column is-three-quarter">
      <Form @aoSalvarTarefa="salvarTarefa"/>
      <div class="list">
        <Tarefa v-for="(tarefa, index) in tarefas" v-bind:key="index" :tarefa="tarefa"/>
      </div>
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import BarraLateral from './components/BarraLateral.vue'
import Tarefa from './components/Tarefa.vue'
import Form from './components/Form.vue'
import ITarefa from './interface/ITarefa'

const tarefas = ref([] as ITarefa [])

const salvarTarefa = (tarefa: ITarefa) => {
  tarefas.value.push(tarefa)
}

</script>

<style scoped>
.list { 
  padding: 1.25rem;
}
</style>

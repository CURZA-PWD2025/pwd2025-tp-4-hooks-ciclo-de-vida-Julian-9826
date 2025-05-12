<script setup lang="ts">
import { ref } from 'vue'

// Importamos los componentes
import Alertas from './components/Alertas.vue'
import Lista from './components/Lista.vue'
import Tareas from './components/Tareas.vue'
import DimensionComponente from './components/DimensionComponente.vue'

// Estado del componente seleccionado
const seleccionado = ref('Alertas')

// Mapeo de nombres a componentes
const componentes: Record<string, any> = {
  Alertas,
  Lista,
  Tareas,
  DimensionComponente,
}
</script>

<template>
  <div style="padding: 20px; font-family: sans-serif;">
    <h1>TP 4 – Ciclo de Vida en Vue</h1>

    <!-- Selector de componente -->
    <label for="componente">Seleccionar componente:</label>
    <select id="componente" v-model="seleccionado">
      <option value="Alertas">Alertas</option>
      <option value="Lista">Lista</option>
      <option value="Tareas">Tareas</option>
      <option value="DimensionComponente">Dimensiones</option>
    </select>

    <hr />

    <!-- Renderizado dinámico -->
    <component :is="componentes[seleccionado]" />
  </div>
</template>

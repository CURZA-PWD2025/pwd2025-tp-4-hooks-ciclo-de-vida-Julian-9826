<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { profesiones } from '../data/profesiones'

const lista = ref<typeof profesiones>([])
const cargando = ref(true)

onMounted(() => {
  setTimeout(() => {
    lista.value = profesiones
    cargando.value = false
  }, 3000)
})
</script>

<template>
  <div>
    <h2>Lista de Profesiones</h2>
    <p v-if="cargando">Cargando...</p>
    <ul v-else>
      <li v-for="p in lista" :key="p.id">
        <strong>{{ p.nombre }}</strong>: {{ p.descripcion }}
      </li>
    </ul>
  </div>
</template>

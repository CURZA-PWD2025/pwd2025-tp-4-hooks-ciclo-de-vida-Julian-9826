<script setup lang="ts">
import { ref, onBeforeUpdate, onUpdated } from 'vue'

const tareas = ref(['Tarea 1', 'Tarea 2'])
const nueva = ref('')
const tareasPrevias = ref([...tareas.value])

onBeforeUpdate(() => {
  console.log('Lista aún no modificada')
  tareasPrevias.value = [...tareas.value]
})

onUpdated(() => {
  console.log('Lista modificada')
})

function agregar() {
  if (nueva.value.trim()) {
    tareas.value.push(nueva.value.trim())
    nueva.value = ''
  }
}
</script>

<template>
  <div>
    <h2>Tareas</h2>
    <input v-model="nueva" placeholder="Nueva tarea" />
    <button @click="agregar">Agregar</button>
    <ul>
      <li
        v-for="(tarea, i) in tareas"
        :key="i"
        :style="{ color: i < tareasPrevias.length ? 'blue' : 'black' }"
      >
        {{ tarea }}
      </li>
    </ul>
  </div>
</template>

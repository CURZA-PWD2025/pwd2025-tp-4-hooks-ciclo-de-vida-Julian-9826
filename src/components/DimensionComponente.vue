<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const ancho = ref(window.innerWidth)
const alto = ref(window.innerHeight)

function actualizar() {
  ancho.value = window.innerWidth
  alto.value = window.innerHeight
}

onMounted(() => {
  window.addEventListener('resize', actualizar)
})

onUnmounted(() => {
  window.removeEventListener('resize', actualizar)
})
</script>

<template>
  <div>
    <h2>Dimensiones de la ventana</h2>
    <p>Ancho: {{ ancho }} px</p>
    <p>Alto: {{ alto }} px</p>
  </div>
</template>

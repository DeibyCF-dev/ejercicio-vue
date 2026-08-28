<script setup>
import { ref } from 'vue'

const nombre = ref('')
const textoInput = ref('')

// Lista de saludos disponibles
const saludos = ['¡Hola!', '!Buenos días!', '¿Qué tal?', 'Qué hubo', 'Bienvenido']
const indiceSaludo = ref(0)

function actualizarSaludo() {
  // 1. Si escribieron algo en el input, actualizamos el nombre
  if (textoInput.value.trim() !== '') {
    nombre.value = textoInput.value
    textoInput.value = ''
  }

  // 2. Cambiamos al siguiente saludo de la lista de forma cíclica
  indiceSaludo.value = (indiceSaludo.value + 1) % saludos.length
}
</script>

<template>
  <div class="contenedor">
    <!-- Combinamos el saludo actual de la lista con el nombre -->
    <h1>{{ saludos[indiceSaludo] }}, {{ nombre }}</h1>
    
    <div class="formulario">
      <input 
        type="text" 
        v-model="textoInput" 
        placeholder="Escribe un nuevo nombre..."
        @keyup.enter="actualizarSaludo"
      />
      <button @click="actualizarSaludo">Cambiar Saludo</button>
    </div>
  </div>
</template>

<style scoped>
.contenedor {
  text-align: center;
  margin-top: 60px;
  font-family: sans-serif;
  color: #2c3e50;
}

.formulario {
  margin-top: 20px;
}

input {
  padding: 8px;
  font-size: 16px;
  margin-right: 10px;
  border-radius: 4px;
  border: 1px solid #ccc;
}

button {
  padding: 8px 16px;
  font-size: 16px;
  background-color: #42b883;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #35495e;
}
</style>
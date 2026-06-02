<script setup>
defineProps({
  nome: {
    type: String,
    default: 'Visitante'
  }
})
</script>

<template>
  <div class="saudacao-output">
    Olá, <span>{{ nome }}</span>! Boas-vindas ao Vue 3 
  </div>
</template>

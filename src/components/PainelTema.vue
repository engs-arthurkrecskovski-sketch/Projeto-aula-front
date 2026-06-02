<script setup>
const emit = defineEmits(['mudouTema'])
</script>

<template>
  <div class="componente-box">
    <div class="componente-tag">PainelTema.vue — emite evento</div>
    <button class="btn-tema" @click="emit('mudouTema', 'claro')">☀️ Claro</button>
    <button class="btn-tema" @click="emit('mudouTema', 'escuro')">🌙 Escuro</button>
    <button class="btn-tema" @click="emit('mudouTema', 'azul')">🔵 Azul</button>
    <button class="btn-tema" @click="emit('mudouTema', 'verde')">🟢 Verde</button>
  </div>
</template>

<script setup>
defineProps({
  tema: {
    type: String,
    default: 'claro'
  }
})
</script>

<template>
  <div class="componente-box">
    <div class="componente-tag">CartaoUsuario.vue — recebe props</div>
    <div :class="['tema-display', `tema-${tema}`]">
      Tema atual: <strong>{{ tema }}</strong>
    </div>
  </div>
</template>

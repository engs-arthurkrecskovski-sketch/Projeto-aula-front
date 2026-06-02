<script setup>
import { ref } from 'vue'

const props = defineProps({
  limite: {
    type: Number,
    default: 5
  }
})

const emit = defineEmits(['limiteAtingido'])

const conta = ref(0)

function incrementar() {
  conta.value++
  if (conta.value === props.limite) {
    emit('limiteAtingido', conta.value)
  }
}

function decrementar() {
  if (conta.value > 0) conta.value--
}

function resetar() {
  conta.value = 0
}
</script>

<template>
  <div class="contador-wrapper">
    <button class="btn-counter secondary" @click="decrementar">−</button>
    <div class="contador-valor">{{ conta }}</div>
    <button class="btn-counter" @click="incrementar">+</button>
    <button class="secondary" style="padding: 6px 12px; font-size: 0.8rem;" @click="resetar">reset</button>
  </div>
  <p class="limite-info">Limite configurado: {{ limite }}</p>
</template>

<script setup>
import { ref } from 'vue'
import SaudacaoPersonalizada from './components/SaudacaoPersonalizada.vue'
import ContadorEmit         from './components/ContadorEmit.vue'
import PainelTema           from './components/PainelTema.vue'
import CartaoUsuario        from './components/CartaoUsuario.vue'

// Exercício 1
const nome = ref('Arthur')

// Exercício 2
const alertaContador = ref(false)
const valorAtingido  = ref(0)

function aoAtingirLimite(valor) {
  valorAtingido.value  = valor
  alertaContador.value = true
  setTimeout(() => (alertaContador.value = false), 3000)
}

// Exercício 3
const temaAtual = ref('claro')
</script>

<template>
  <div class="app-header">
    <h1>Vue 3 — Prática de Componentes</h1>
    <p>Props, Eventos e Integração entre componentes</p>
  </div>

  <div class="exercicios">

    <!-- Exercício 1 -->
    <div class="card">
      <div class="card-numero">1</div>
      <div class="card-titulo">Saudação personalizada via props</div>
      <h2>Componente filho</h2>
      <SaudacaoPersonalizada :nome="nome" />
      <h2>Controle do pai</h2>
      <input
        v-model="nome"
        type="text"
        placeholder="Digite um nome..."
      />
    </div>

    <!-- Exercício 2 -->
    <div class="card">
      <div class="card-numero">2</div>
      <div class="card-titulo">Contador com emit ao atingir limite</div>
      <h2>Componente filho</h2>
      <ContadorEmit :limite="5" @limiteAtingido="aoAtingirLimite" />
      <div v-if="alertaContador" class="alerta">
        ✓ Evento recebido pelo pai — limite {{ valorAtingido }} atingido!
      </div>
    </div>

    <!-- Exercício 3 -->
    <div class="card">
      <div class="card-numero">3</div>
      <div class="card-titulo">Integração: filho A emite → pai → filho B recebe</div>
      <h2>Componentes filhos</h2>
      <div class="integracao-grid">
        <PainelTema   @mudouTema="t => temaAtual = t" />
        <CartaoUsuario :tema="temaAtual" />
      </div>
    </div>

  </div>
</template>

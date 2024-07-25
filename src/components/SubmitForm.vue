<script setup>
defineProps({
  nome: {
    type: String,
    required: true
  },
  email: {
    type: String,
    required: true

  },
  senha: {
    type: String,
    required: true
  },
  confirma: {
    type: String,
    required: true
  },
  data: {
    type: String,
    required: true
  },
  endereco: {
    type: String,
    required: true
  },
  cidade: {
    type: String,
    required: true
  },
  hobbies: {
    type: String,
    required: true
  },
  biografia: {
    type: String,
    required: true
  },
  linguagens: {
    type: Array,
    required: true
  }
})



</script>
<template>
  <div class="botao">


    <div class="resultado">
      <p>Nome: {{ nome }}</p>
      <p>E-mail: {{ email }}</p>
      <p>Senha: {{ senha }}</p>
      <p>Data de Nascimento: {{ data }}</p>
      <p>Endereço: {{ endereco }}</p>
      <p>Cidade: {{ cidade }}</p>
      <p>Hobbies: {{ hobbies }}
      </p>
      <p>Biografia: {{ biografia }}</p>
      <p>Linguagens Preferidas: <span v-for="linguagem, i in linguagens" :key="i">{{ linguagem }}</span></p>
    </div>

    
  </div>
</template>

<style scoped></style>
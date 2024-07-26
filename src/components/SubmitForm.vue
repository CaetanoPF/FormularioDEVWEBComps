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

const emits = defineEmits([
  'voltar'
])

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
      <p>Hobbies: {{ hobbies }}</p>
      <p>Biografia: {{ biografia }}</p>
      <p>Linguagens Preferidas: <span v-for="linguagem, i in linguagens" :key="i">{{ linguagem }}</span></p>
    </div>

  </div>
</template>

<style scoped>
.resultado {
  color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 500px;
}

button {
  background: #223243;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 25px;
  box-shadow: -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35);
  padding: 12px 10px 12px 10px;
  border: none;
  color: rgb(20, 250, 70);
  display: flex;
  flex-direction: column;
  margin-top: 20px;
  font-family: Amarante, serif;
}

.resultado p {
  color: rgb(20, 250, 70);
}

.botao {
  width: 100%;
  height: 60%;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50vw;
  padding: 40px;
  border-radius: 20px;
  border: 8px solid #223243;
  box-shadow: -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35),
    inset -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35),
    inset -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35);
  width: 60vw;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 25px;
  color: #FFF;
  background-color: #223243;
}
</style>
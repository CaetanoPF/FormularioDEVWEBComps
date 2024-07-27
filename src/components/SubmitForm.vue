
<script setup>
const emits = defineEmits([
  'voltar'
])
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
      <p>Hobbies: {{ hobbies }}</p>
      <p>Biografia: {{ biografia }}</p>
      <p>Linguagens Preferidas: <span v-for="linguagem, i in linguagens" :key="i">{{ linguagem }}</span></p>
      <div>
        <button @click="emits('voltar')">voltar</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

* {
  font-family: "Roboto", sans-serif;
  font-weight: 500;
}

.resultado {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  margin: 0vw 0vw 0vw 0vw;
  padding: 1vw 0vw 0vw 0vw;
}

button {
  background: #ffffff;
  border-radius: 1vw;
  box-shadow: -5px -5px 15px rgba(221, 221, 221, 0.336), 5px 5px 15px rgba(156, 156, 156, 0.301);
  padding: 1vw 5vw 1vw 5vw;
  margin: 2vw 0vw 0vw 0vw;
  border: none;
  font-weight: 600;
}

.botao {
  width: 100%;
  height: 70%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border-radius: 5vw; 
  box-shadow: 1vw -0.5vw 2vw #dbdbdbce,
    -1vw 0vw 2vw #fafafa; 
  gap: 25px; 
  background-color: #ffffff;
}
</style>
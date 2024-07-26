<script setup>
import { reactive, ref } from 'vue';
import SubmitForm from './SubmitForm.vue';
const linguagens = ref('');

const mostrarResult = ref(true)
function addlang() {
    if (linguagens.value == '' || !infos.email.includes('@') || infos.confirma != infos.senha) {
        alert('Credenciais inválidas!')
    }
    else {
        infos.linguagens.push(linguagens.value)
        mostrarResult.value = !mostrarResult.value
    }
    console.log(infos)
}

const infos = reactive({
    nome: '',
    email: '',
    senha: '',
    confirma: '',
    data: '',
    endereco: '',
    cidade: '',
    hobbies: '',
    biografia: '',
    linguagens: []
})


const estado = ref('');
const states = reactive([
    { uf: 'AC -', name: 'Acre' },
    { uf: 'AL -', name: 'Alagoas' },
    { uf: 'AP -', name: 'Amapá' },
    { uf: 'AM -', name: 'Amazonas' },
    { uf: 'BA -', name: 'Bahia' },
    { uf: 'CE -', name: 'Ceará' },
    { uf: 'DF -', name: 'Distrito Federal' },
    { uf: 'ES -', name: 'Espírito Santo' },
    { uf: 'GO -', name: 'Goiás' },
    { uf: 'MA -', name: 'Maranhão' },
    { uf: 'MT -', name: 'Mato Grosso' },
    { uf: 'MS -', name: 'Mato Grosso do Sul' },
    { uf: 'MG -', name: 'Minas Gerais' },
    { uf: 'PA -', name: 'Pará' },
    { uf: 'PB -', name: 'Paraíba' },
    { uf: 'PR -', name: 'Paraná' },
    { uf: 'PE -', name: 'Pernambuco' },
    { uf: 'PI -', name: 'Piauí' },
    { uf: 'RJ -', name: 'Rio de Janeiro' },
    { uf: 'RN -', name: 'Rio Grande do Norte' },
    { uf: 'RS -', name: 'Rio Grande do Sul' },
    { uf: 'RO -', name: 'Rondônia' },
    { uf: 'RR -', name: 'Roraima' },
    { uf: 'SC -', name: 'Santa Catarina' },
    { uf: 'SP -', name: 'São Paulo' },
    { uf: 'SE -', name: 'Sergipe' },
    { uf: 'TO -', name: 'Tocantins' }
]);
</script>

<template>
    <h2>{{ titulo }}</h2>
    <div class="container" v-if="mostrarResult">
        <div class="formulario">
            <h2>Cadastre-se</h2>

            <div class="row">
                <label for="">Nome:</label>
                <input type="text" v-model="infos.nome" placeholder="Primeiro nome" required>
            </div>

            <div class="row">
                <label for="">E-mail:</label>
                <input type="text" v-model="infos.email" placeholder="Email pessoal" required>
            </div>

            <div class="row">
                <label for="">Senha:</label>
                <input type="password" v-model="infos.senha" placeholder="Informe uma senha" required>
            </div>

            <div class="row">
                <label for="">Confirmação de senha:</label>
                <input type="password" v-model="infos.confirma" placeholder="Confirme sua senha" required>

            </div>
            <div class="row">
                <label for="">Data de nascimento:</label>
                <input type="date" v-model="infos.data" required>
            </div>
            <div class="row">
                <label for="">Endereço:</label>
                <input type="text" v-model="infos.endereco" placeholder="Seu endereço" required>
            </div>
            <div class="row">
                <label for="">Cidade:</label>
                <input type="text" v-model="infos.cidade" placeholder="Cidade em que reside" required>
            </div>
            <div class="row">
                <label for="text">Estado:</label>
                <select name="estados" id="estados" v-model="estado" placeholder="Estado em que reside" required>
                    <option value="" disabled selected>Informe o estado em que reside</option>
                    <option value="state.uf" v-for="state in states" :key="state.uf"> {{ state.uf }} {{ state.name }}
                    </option>
                </select>
            </div>
            <div class="row">
                <label for="">Hobbies:</label>
                <input type="text" v-model="infos.hobbies" placeholder="O que mais gosta de fazer" required>
            </div>
            <div class="row">
                <label for="">Biografia:</label>
                <input type="text" v-model="infos.biografia" placeholder="Pequena biografia" required>
            </div>
            <div class="row">
                <label for="">Linguagens:</label>
                <input type="text" v-model="linguagens" placeholder="Linguagens de porgramação favoritas" required>

                <div class="botao">
                    <button @click="addlang">Salvar</button>
                </div>
            </div>
        </div>
    </div>
    <div v-else class="result">
        <SubmitForm :nome="infos.nome" :email="infos.email" :senha="infos.senha" :data="infos.data"
            :endereco="infos.endereco" :cidade="infos.cidade" :hobbies="infos.hobbies" :biografia="infos.biografia"
            :linguagens="infos.linguagens" @voltar="mostrarResult = !mostrarResult" />
    </div>
</template>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

* {
    font-family: "Roboto", sans-serif;
}

.botao {
    display: flex;
    justify-content: center;
    padding: 20px;
    border: none;
}

.container {
    width: 100%;
    border-radius: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
}

h2 {
    display: flex;
    justify-content: center;
    margin-top: 1rem;
}

.container,
.formulario {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 25px;
}

.container .formulario h2 {
    font-weight: 500;
    letter-spacing: 0.1rem;
}

.container,
.formulario,
.row {
    position: relative;
    width: 80%;
}

.formulario .row {
    margin: 1.3rem 0;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 80%;
}

.result {
    width: 50vw;
    padding: 40px;
    width: 60vw;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 25px;
    height: 100vh;
}

.formulario {
    border: none;
    width: 40vw;
    font-weight: 300;
    border-radius: 25px;
    font-size: 1.1vw;
    background: #ffffff;
    box-shadow: 1vw -0.5vw 1vw #e4e4e4ce,
        -1vw 0vw 1vw #f1f1f1;
    transition: 0.5s;
    outline: none;
}

input,
select {
    border-radius: 25px;
    background: #ffffff;
    box-shadow: 1vw 1vw 1vw #ececec,
        -1vw -1vw 4vw #ececec;
    padding: 1vw 1vw 1vw 1vw;
    border: none;
}

.items-checkbox {
    display: flex;
    flex-direction: column;
}

button {
    width: 20%;
    background: #f8f8f8;
    border-radius: 25px;
    box-shadow: -5px -5px 15px rgba(221, 221, 221, 0.336), 5px 5px 15px rgba(156, 156, 156, 0.301);
    padding: 1vw 2vw 1vw 2vw;
    margin: 1vw;
    border: none;
}
</style>
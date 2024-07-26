<script setup>
import { reactive, ref } from 'vue';
import SubmitForm from './SubmitForm.vue';
const linguagens = ref('');

const mostrarResult = ref(true)
function addlang() {
    if (linguagens.value == '' || !infos.email.includes('@') || infos.confirma != infos.senha) {
        alert('Preencha todos campo CORRETAMENTE')
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
                <input type="text" v-model="infos.nome">
            </div>

            <div class="row">
                <label for="">E-mail:</label>
                <input type="text" v-model="infos.email">
            </div>

            <div class="row">
                <label for="">Senha:</label>
                <input type="password" v-model="infos.senha">
            </div>

            <div class="row">
                <label for="">Confirmação de senha:</label>
                <input type="password" v-model="infos.confirma">

            </div>
            <div class="row">
                <label for="">Data de nascimento:</label>
                <input type="date" v-model="infos.data">
            </div>
            <div class="row">
                <label for="">Endereço:</label>
                <input type="text" v-model="infos.endereco">
            </div>
            <div class="row">
                <label for="">Cidade:</label>
                <input type="text" v-model="infos.cidade">
            </div>
            <div class="row">
                <label for="text">Estado:</label>
                <select name="estados" id="estados" v-model="estado">
                    <option value="state.uf" v-for="state in states" :key="state.uf"> {{ state.uf }} {{ state.name }}
                    </option>
                </select>
            </div>
            <div class="row">
                <label for="">Hobbies:</label>
                <input type="text" v-model="infos.hobbies">
            </div>
            <div class="row">
                <label for="">Biografia:</label>
                <input type="text" v-model="infos.biografia">
            </div>
            <div class="row">
                <label for="">Diga quais são suas linguagens preferidas:</label>
                <input type="text" v-model="linguagens">

                <div class="botao">
                    <button @click="addlang">Salvar</button>

                </div>
            </div>

        </div>
        <div class="footer">

            <p>Todos os direitos reservados Bokorni Corporation©</p>

        </div>
    </div>
    <div v-else class="result">
        <SubmitForm :nome="infos.nome" :email="infos.email" :senha="infos.senha" :data="infos.data"
            :endereco="infos.endereco" :cidade="infos.cidade" :hobbies="infos.hobbies" :biografia="infos.biografia"
            :linguagens="infos.linguagens" @voltar="mostrarResult = !mostrarResult"/>

    </div>
</template>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Amarante&display=swap');

* {
    font-family: "Amarante", serif;
}

.botao {
    
    display: flex;
    justify-content: center;
    padding: 20px;
    border: none;
    color: rgb(0, 0, 0);

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
    color: rgb(0, 0, 0);
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

.footer {
    background-color: #223243;
    width: 80%;
    height: 150px;
    font-size: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: rgb(0, 0, 0);
    border-radius: 20px;
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
    color: #FFF;
    height: 100vh;
}

.formulario {
    padding: 12px 10px 12px 48px;
    border: none;
    width: 60vw;
    background: #223243;
    border: 1px solid rgba(0, 0, 0, 0.1);
    color: #FFF;
    font-weight: 300;
    border-radius: 25px;
    font-size: 1em;
    box-shadow: -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35);
    transition: 0.5s;
    outline: none;
}

input,
select {
    background: #223243;
    border: 1px solid rgba(0, 0, 0, 0.1);
    border-radius: 25px;
    box-shadow: -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35);
    padding: 12px 10px 12px 48px;
    border: none;
    color: rgb(255, 255, 255);
}

.check {
    width: 2vw;
}

.items-checkbox {
    display: flex;
    flex-direction: column;
}

button {
    background: #223243;
    border: 1px solid rgba(0, 0, 0, 0.1);
    border-radius: 25px;
    box-shadow: -5px -5px 15px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.35);
    padding: 12px 10px 12px 10px;
    border: none;
    color: rgb(20, 250, 70);
}
</style>
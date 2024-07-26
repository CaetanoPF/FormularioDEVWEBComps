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
        linguagens.value = ''
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
    <div class="container" v-if="mostrarResult">

        <div class="formulario">
            <h2>Cadastre-se</h2>

            <div class="row">
                <label for="">Nome:</label>
                <input type="text" v-model="infos.nome" placeholder="Informe seu nome" required />
            </div>

            <div class="row">
                <label for="">E-mail:</label>
                <input type="text" v-model="infos.email" placeholder="Informe seu email" required />
            </div>

            <div class="row">
                <label for="">Senha:</label>
                <input type="password" v-model="infos.senha" placeholder="Crie uma senha" required />
            </div>

            <div class="row">
                <label for="">Confirmação de senha:</label>
                <input type="password" v-model="infos.confirma" placeholder="Confirme sua senha" required />

            </div>
            <div class="row">
                <label for="">Data de nascimento:</label>
                <input type="date" v-model="infos.data" placeholder="Sua data de nascimento" required />
            </div>
            <div class="row">
                <label for="">Endereço:</label>
                <input type="text" v-model="infos.endereco" placeholder="Seu endereço" required />
            </div>
            <div class="row">
                <label for="">Cidade:</label>
                <input type="text" v-model="infos.cidade" placeholder="Cidade em que reside" required />
            </div>
            <div class="row">
                <label for="text">Estado:</label>
                <select name="estados" id="estados" v-model="estado" placeholder="Informe o estado em que reside" required >
                    <option value="" disabled selected>Informe o estado em que reside</option>
                    <option value="state.uf" v-for="state in states" :key="state.uf" > {{ state.uf }} {{ state.name }} </option>
                </select>
            </div>
            <div class="row">
                <label for="">Hobbies:</label>
                <input type="text" v-model="infos.hobbies" placeholder="Informe seus hobbies" required />
            </div>
            <div class="row">
                <label for="">Biografia:</label>
                <input type="text" v-model="infos.biografia" placeholder="Breve biografia" required />
            </div>
            <div class="row">
                <label for="">Diga quais são suas linguagens preferidas:</label>
                <input type="text" v-model="linguagens">
            </div>
            <div class="botao">
                <button @click="addlang">Salvar</button>
            </div>
        </div>
        <div class="result">
        </div>
    </div>
    <div v-else class="result">
        <SubmitForm :nome="infos.nome" :email="infos.email" :senha="infos.senha" :data="infos.data"
            :endereco="infos.endereco" :cidade="infos.cidade" :hobbies="infos.hobbies" :biografia="infos.biografia"
            :linguagens="infos.linguagens" />
    </div>
</template>

<style scoped>
button {
    border-radius: 10%;
    border: none;
    padding: 0.7em 1.7em;
    font-size: 18px;
    border-radius: 0.5em;
    background: #e8e8e8;
    cursor: pointer;
    border: 1px solid #e8e8e8;
    background: #fafafa;
    box-shadow: 12px 12px 24px #cbcbcb,
        -12px -12px 24px #ffffff;
    transition: all 0.3s;
}

button:hover {
    border: 1px solid rgb(207, 207, 207);
}

.container {
    display: flex;
    justify-content: center;
    flex-direction: column;
    width: 100%;
    box-shadow: 12px 12px 24px #cbcbcb,
        -12px -12px 24px #ffffff;
}

label {
    color: #000000;
}

.formulario {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.container,
.formulario,
.row {
    background: #e6e6e6;
    position: relative;
    align-items: center;
    color: #000000;
}

.formulario .row {
    margin: 1.3rem 0;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 50%;
}

.result {
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 50vw;
    padding: 40px;
    border-radius: 20px;
    width: 60vw;
    gap: 25px;
}

.formulario {
    border: none;
    width: 50%;
    font-weight: 20px;
    border-radius: 25px;
    font-size: 1em;
    transition: 0.5s;
    outline: none;
}

input,
select {
    background: #ffffff;
    width: 100%;
    height: 3vh;
    border-radius: 10px;
    padding: 10px;
    border: none;
    color: rgb(0, 0, 0);
}

.items-checkbox {
    display: flex;
    flex-direction: column;
    color: #000000;
}
</style>
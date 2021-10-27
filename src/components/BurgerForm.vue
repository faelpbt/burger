<template>
   <div>
    <h1 class="text-xl">componente de menssagem</h1>
    <div>
        <form id="burger-form" @submit="createBurger">
            <div class="input-container">
                <label for="nome">Nome do cliente:</label>
                <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite seu nome">
            </div>
            <div class="input-container">
                <label for="nome">Escolha o pão:</label>
                <select for="pao" id="pao" v-model="pao">
                    <option value="">Selecione o seu pão</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
                </select>
            </div>
            <div class="input-container">
                <label for="nome">Escolha a carne:</label>
                <select for="carne" id="carne" v-model="carne">
                    <option value="">Selecione o seu pão</option>
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                </select>
            </div>
            <div id="opcionais-container" class="imput-container">
                <label id="opcionais-title" for="opcionais">Escolha os opcionais:</label>
                    <div class="checkbox-container" v-for="opcional in opcionaisData" :key="opcional.id" >
                        <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                        <span>{{ opcional.tipo }}</span>
                    </div>
            </div>
            <div class="input-container">
                <input type="submit" class="submit-btn" value="Criar meu Burger!">
            </div>
        </form>
    </div>
   </div>
</template>

<script>
    export default {
        name: 'BurgerForm',
        data() {
            return {
                paes: null,
                carnes: null,
                opcionaisData: null,
                nome: null,
                pao: null,
                carne: null,
                opcionais: [],
                msg: null,
            }
        },
        methods: {
            async getIngredientes() {
                const req = await fetch('http://localhost:3000/ingredientes');
                const data = await req.json();

                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisData = data.opcionais;
            },

            async createBurger(e) {
                
                e.preventDefault();

                const data = {
                    nome: this.nome,
                    carne: this.carne,
                    pao: this.pao,
                    opcionais: Array.from(this.opcionais),
                    status: 'Solicitado',

                }

                const dataJson = JSON.stringify(data);

                const req = await fetch('http://localhost:3000/burgers', {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: dataJson
                });

                const res = await req.json();

                // colocar uma mensagem no sistema

                // limpar os campos

                this.nome = '',
                this.carne = '',
                this.pao = '',
                this.opcionais = '',

            }
        },
        mounted() {
            this.getIngredientes()
        },
    }
</script>

<style lang="postcss" scoped>
#burger-form{
    @apply w-96 mx-auto;
}
.input-container{
    @apply flex flex-col mb-5;
}
label{
    @apply font-bold mb-3 py-1.5 px-2.5 border-l-4;
    color: #222;
    border-color: #FCBA03;
}
input, select{
    @apply py-1.5 px-2.5 w-72 border;
}
#opcionais-container {
    @apply flex flex-row flex-wrap;
}
#opcionais-title {
    @apply w-full;
}
.checkbox-container{
    @apply flex items-center w-1/2 mb-5;
}
.checkbox-container span,
.checkbox-container input {
    @apply w-auto;
}
.checkbox-container span {
    @apply ml-1.5 font-bold;
}
.submit-btn{
    @apply font-bold border-2 p-2.5 text-base mx-auto cursor-pointer;
    background-color: #222;
    border-color: #222;
    color: #FCBA03;
    transition: .5s;
}
.submit-btn:hover{
    @apply bg-transparent;
    color: #222;
}
</style>
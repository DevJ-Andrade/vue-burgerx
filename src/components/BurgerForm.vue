
```
<template>
<div>
    <Message :msg="msg" v-show="msg" />
    <div>
        <form id="burger-form" @submit="createBurger">
            <div class="input-container">
                <label for="nome">Client's name</label>
                <input type="text" id="nome" name="name" v-model="nome" placeholder="Type your name">
            </div>
            <div class="input-container">
                <label for="pao">Choose bread</label>
                <select name="pao" id="pao" v-model="pao">
                    <option value="">Choose your Bread</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo}}</option>
                </select>
            </div>
            <div class="input-container">
                <label for="carne">Choose your favorite meat</label>
                <select name="carne" id="carne" v-model="carne">
                        
                    <option value="">Choose your meat</option>
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo}}</option>
                </select>
            </div>
            <div id="optional-container" class="input-container">
                <label for="opcional" id="optional-title">Select the options</label>
            <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id" >
                <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo"> 
                <span>{{opcional.tipo}}</span>
            </div>
            </div>
            <div class="input-container">
                <input type="submit" class="submit-btn" value="Make my BurgerX">
            </div>
        </form>
    </div>
</div>
</template>
<script>
//import Banner from './Banner.vue';
//import BurgerForm from './BurgerForm.vue';
import Message from './Message.vue';
export default {
    name: "BurgerForm",
    data() {
        return {
            paes: null,
            carnes: null,
            opcionaisdata: null,
            nome: null,
            pao: null,
            carne: null,
            optional: [],
            msg: null
        }
    },
    methods: {
        async getIngredientes() {
            const req = await fetch("http://localhost:3000/ingredientes");
            const data = await req.json();
            this.paes = data.paes
            this.carnes = data.carnes
            this.opcionaisdata = data.opcionais
        },
        async createBurger(e) {
            e.preventDefault();
            const data = {
                nome: this.nome,
                carne: this.carne,
                bread: this.pao,
                opcionais: Array.from(this.opcionais),
                status: "Solicitado"
            };
            
            //Inserido dados no banco
            const dataJson = JSON.stringify(data);
            const req = await fetch("http://localhost:3000/burgers", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: dataJson
            });
            const res = await req.json();
            //Colocar uma msg de sistema
            this.msg = `Pedido Nº ${res.id} Pedido realizado com sucesso ` 
            //Limpar msg 
            setTimeout(() => this.msg="", 3000);
            // Limpar os campos do form front
            this.nome = "",
            this.carne = "";
            this.pao = "";
            this.optional = []
        }
    },
    mounted() {
        this.getIngredientes();
    },
    components: {
        Message 
}
}
</script>
<style scoped>
#burger-form {
    max-width: 400px;
    margin: 0 auto;
}
.input-container {
    display:flex;
    flex-direction: column;
    margin-bottom: 20px;
}
label {
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid #FCBA03;
}
input, select {
    padding: 5px 10px;
    width: 300px;
}
#optional-container {
flex-direction: row;
flex-wrap: wrap;
}
#optional-title {
    width: 100%;
}
.checkbox-container {
    display:flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
}
.checkbox-container span,
.checkbox-container input {
    width: auto;
}
.checkbox-container span {
    margin-left: 6px;
    font-weight: bold;
}
.submit-btn {
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
}
.submit-btn:hover {
    background-color: transparent;
    color: #222;
}
</style>
```

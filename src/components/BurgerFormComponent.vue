<template>
  <div>
    <MessageComponent :msg="msg" v-show="msg" />
    <div>
      <form id="burger-form" @submit="createBurger">
        <div class="input-container">
          <label for="nome">Nome do Cliente</label>
          <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
        </div>

        <div class="input-container">
          <label for="pao">Escolha o Pão:</label>
          <select name="pao" id="pao" v-model="pao">
            <option value="">Selecione seu pão</option>
            <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
          </select>
        </div>

        <div class="input-container">
          <label for="carne">Escolha a Carne do seu Burger:</label>
          <select name="carne" id="carne" v-model="carne">
            <option value="">Selecione o tipo de carne</option>
            <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
          </select>
        </div>

        <div id="opcionais-container" class="input-container">
          <label for="opcionais">Selecione os Opcionais:</label>
          <div class="checkbox-container" v-for="opcional in opcionaisData" :key="opcional.id">
            <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
            <span>{{ opcional.tipo }}</span>
          </div>
        </div>

        <div class="input-container">
          <input type="submit" class="btn-submit" value="Criar meu Burger!">
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import MessageComponent from "./MessageComponent.vue";

export default {
  components: {
    MessageComponent
  },
  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisData: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      msg: null
    }
  },
  mounted() {
    this.getIngredientes();
  },
  methods: {
    async getIngredientes() {

      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisData = data.opcionais;
    },

    async createBurger(e) {

      e.preventDefault();

      const data = {
        nome: this.nome,
        pao: this.pao,
        carne: this.carne,
        opcionais: Array.from(this.opcionais),
        status: "Solicitado"
      };
      const dataJson = JSON.stringify(data);
      const req = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: dataJson
      });
      const res = await req.json();

      this.msg = `Pedido nº ${res.id} realizado com sucesso`;
      setTimeout(() => this.msg = "", 3000);

      this.nome = "";
      this.pao = "";
      this.carne = "";
      this.opcionais = "";
    }
  }
}
</script>

<style scoped>
#burger-form {
  max-width: 400px;
  margin: 0 auto;
}

.input-container {
  display: flex;
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

input,
select {
  padding: 5px 10px;
}

#opcionais-container {
  flex-direction: row;
  flex-wrap: wrap;
}

.checkbox-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}

.checkbox-container span {
  margin-left: 6px;
  font-weight: bold;
}

.btn-submit {
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

.btn-submit:hover {
  background-color: transparent;
  color: #222;
}
</style>
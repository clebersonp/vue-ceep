<template>
  <div id="app">
    <Header :showOption="true" :carrega-cartao="carregaCartao"/>
    <Formulario :show-option="true"/>
    <Cartao :show-option="true" v-for="ajuda in ajudas" 
      :id="ajudas.indexOf(ajuda)" :cor="ajuda.cor" :conteudo="ajuda.conteudo"
      :key="ajudas.indexOf(ajuda)"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Formulario from "./components/Formulario.vue";
import Cartao from "./components/Cartao.vue";

export default {
  name: "app",
  components: {
    Header,
    Formulario,
    Cartao
  },
  data: function() {
    return {
      ajudas: null
    }
  },
  methods: {
    carregaCartao: function() {
      this.$http.get("https://ceep.herokuapp.com/cartoes/instrucoes").then(
        response => {
          // get body data
          this.someData = response.body;
          console.log(this.someData)
          this.ajudas = this.someData.instrucoes
        },
        response => {
          // error callback
        }
      );
    }
  }
};
</script>

<style>
/* reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box; /* controla o tamanho total do elemento html */
}

body {
  background: #e8e8e8;
}

:focus {
  outline-color: #3b99fc;
  outline-style: solid;
  outline-width: 3px;
}

/* container */
.container {
  padding: 0 10%;
}
</style>

<template>
  <div id="app">
    <Header :showOption="true"/>
    <Formulario :show-option="true"/>
    <Cartao :show-option="true" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Formulario from './components/Formulario.vue'
import Cartao from './components/Cartao.vue'

export default {
  name: 'app',
  components: {
    Header,
    Formulario,
    Cartao
  }
}
</script>

<style>
/* reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box; /* controla o tamanho total do elemento html */
}

body {
  background: #E8E8E8;
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

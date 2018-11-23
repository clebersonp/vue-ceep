<template>
  <header class="cabecalho container">
      <h1 class="cabecalho-logo">
        Ceep
      </h1>
      <div v-if="showOption" class="opcoesDaPagina">
        <input type="search" placeholder="busca" id="busca" class="opcoesDaPagina-opcao">
        <button id="btnMudaLayout" class="opcoesDaPagina-opcao opcoesDaPagina-botao">
          Linhas
        </button>
        <button id="btnAjuda" class="opcoesDaPagina-opcao opcoesDaPagina-botao" v-on:click="carregaCartao">
          ?
        </button>
        <button id="btnSync"  class="opcoesDaPagina-opcao opcoesDaPagina-botao botaoSync botaoSync--sincronizado">
          <svg class="botaoSync-icone">
            <use xlink:href="#iconeSincronizar"></use>
          </svg>
        </button>
      </div>
    </header>
</template>

<script>

  /*
    baixar as dependencias: npm install -> dentro do diretorio do projeto que tem o package.json
    subir o server: npm run serve
   */

  export default {
    name: "Header",
    props: {
      showOption: Boolean,
      carregaCartao: Function
    },
    methods : {
      print: function() {
        console.log("CEE")
      }
    }
  }
</script>

<style scoped>

/* botao sync */
.botaoSync {
	line-height: 0;
	border-radius: 50%;
	color: white;
}

.botaoSync-icone {
	fill: currentcolor;
	width: 1em; 
	height: 1em;
}

@keyframes rodaRodaJequiti {
	to {
		transform: rotate(180deg);
	}
}

.botaoSync--deuRuim {
	background: #ED7F6C;
}

.botaoSync--esperando {
	animation: rodaRodaJequiti .5s linear infinite;
}

.botaoSync--sincronizado {
	background: #39B5AC;
}

/* cabecalho */
.cabecalho {
	background-color: #0082C7;
	font-size: 1rem;
	padding-top: .5em;
	padding-bottom: .5em;
	text-align: center;
	display: flex;
	flex-wrap: wrap;
	justify-content: space-between;
	align-items: center;
	align-content: center;
}

.cabecalho-logo {
	font-size: 2em;
	margin-bottom: .3em;
	font-family: "Verdana", "Helvetica", sans-serif;
	color: rgba(255,255,255,.7);
	display: inline-block;
	vertical-align: middle;
	margin-right: 1em;
	margin-bottom: 0;
}

/* opcoes da pagina */
.opcoesDaPagina {
	display: inline-block;
	vertical-align: middle;
	font-size: 1rem;
	flex: 1;
	text-align: right;
}

.opcoesDaPagina-opcao {
	font-size: 1em;
	vertical-align: middle;
	font-family: "Lucida Grande", "Helvetica", "Arial", sans-serif;
}

.opcoesDaPagina-opcao + .opcoesDaPagina-opcao {
	margin-left: 1em;
}

.opcoesDaPagina-botao {
	padding: .5em;
	max-width: 4.5em;
	border: none;
	background: rgba(0,0,0,.25);
	color: white;
}

.opcoesDaPagina-opcao#busca {
	border: none;
	padding: .2em;
	width: 100%;
	max-width: 200px;
}

.opcoesDaPagina-opcao#mudaLayout {
  display: none;
}

@media (min-width: 610px){

	.opcoesDaPagina-opcao#mudaLayout{
		display: inline-block;
	}

}

</style>
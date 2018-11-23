<template>
    <section class="container mural" style="font-size: 1.3rem;">
        <article :id="`cartao_${idCartao}`" class="cartao" tabindex="0" style="background-color:${cor}">
            <div class="opcoesDoCartao">
                <button class="opcoesDoCartao-remove opcoesDoCartao-opcao" tabindex="0">
                <svg><use xlink:href="#iconeRemover"></use></svg>
                </button>

                <input type="radio" name="corDoCartao1" value="#EBEF40" id="corPadrão-cartao1" class="opcoesDoCartao-radioTipo" checked>
                <label for="corPadrão-cartao1" class="opcoesDoCartao-tipo opcoesDoCartao-opcao" style="color: #EBEF40;" tabindex="0">
                    Padrão
                </label>

                <input type="radio" name="corDoCartao1" value="#F05450" id="corImportante-cartao1" class="opcoesDoCartao-radioTipo">
                <label for="corImportante-cartao1" class="opcoesDoCartao-tipo opcoesDoCartao-opcao" style="color: #F05450;" tabindex="0">
                    Importante
                </label>

                <input type="radio" name="corDoCartao1" value="#92C4EC" id="corTarefa-cartao1" class="opcoesDoCartao-radioTipo">
                <label for="corTarefa-cartao1" class="opcoesDoCartao-tipo opcoesDoCartao-opcao" style="color: #92C4EC;" tabindex="0">
                    Tarefa
                </label>

                <input type="radio" name="corDoCartao1" value="#76EF40" id="corInspiração-cartao1" class="opcoesDoCartao-radioTipo">
                <label for="corInspiração-cartao1" class="opcoesDoCartao-tipo opcoesDoCartao-opcao" style="color: #76EF40;" tabindex="0">
                    Inspiração
                </label>
            </div>
            <p class="cartao-conteudo" contenteditable tabindex="0">Conteudo do cartão</p>
        </article>
    </section>
</template>

<script>
export default {
  name: "Cartao",
  props: {
    showOption: Boolean,
    conteudo: String,
    idCartao: Number,
    cor: String
  },
  methods: {
    print: function() {
      console.log("Cartao");
    }
  }
};
</script>

<style>
/*  mural */
.mural {
  font-size: 1.2rem;
}

@media (min-width: 560px) {
  .mural {
    text-align: center;
    display: flex;
    flex-wrap: wrap;
    align-items: flex-start;
    justify-content: space-around;
  }

  .mural--linha {
    flex-direction: column;
  }

  .mural--linha .cartao {
    flex-basis: auto;
    width: auto;
  }
}

@media (min-width: 900px) {
  .mural {
    align-items: center;
    font-size: 1.3rem;
  }
}

/* cartao */
.cartao {
  margin: 32px 16px;
  padding: 16px;
  line-height: 1.5;
  overflow: visible;
  position: relative;
  word-wrap: break-word;
  font-family: "Lucida Grande", "Helvetica", "Arial", sans-serif;
  background: #ebef40;
  box-shadow: 1px 1px 1px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s ease-in;
}

.cartao--some {
  opacity: 0;
  transition: 0.5s;
}

.cartao--muda--cor {
  transition: 0.2s ease-in;
}

.cartao.cartao--focado,
.cartao:hover,
.cartao:focus {
  transform: scale(1.1);
  z-index: 2;
}

/* .cartao .opcoesDoCartao-opcao {
	opacity: 0;
	transition: opacity .2s ease;
}

.cartao:focus .opcoesDoCartao-opcao,
.cartao--focado .opcoesDoCartao-opcao{
	opacity: 1;
} */

.cartao-conteudo {
  white-space: pre-line;
  max-height: 400px;
  overflow: hidden;
  font-size: 1em;
}

.cartao-conteudo * {
  font-size: 1em !important; /*desculpa a gente*/
}

.cartao-conteudo img {
  width: 100%;
}

.cartao:hover .cartao-conteudo,
.cartao:focus .cartao-conteudo,
.cartao-conteudo:focus {
  overflow: auto;
}

.opcoesDoCartao {
  font-size: 1rem;
  position: absolute;
  top: 0;
  left: 0;
  transform: translate(-1em, -50%);
  white-space: nowrap;
}

.opcoesDoCartao-opcao {
  display: inline-block;
  vertical-align: middle;
  font-size: 1em;
  height: 2em;
  width: 2em;
  overflow: hidden;
  text-align: center;
  box-sizing: border-box;
  border-radius: 50%;
  border: 2px solid;
  border-color: #aeaeae;
  background-color: #eeeeee;
  background-size: 1em 1em;
  background-position: center center;
  background-repeat: no-repeat;
  text-indent: -99999px;
}

.opcoesDoCartao-opcao:first-child {
  margin-right: 0.5em;
}

.opcoesDoCartao-fecha {
  /*background-image: url("../img/close.svg");*/
}

.opcoesDoCartao-remove {
  /*background-image: url("../img/bin2.svg");*/
}

.opcoesDoCartao-edita {
  /*background-image: url("../img/edit.svg");*/
}

.opcoesDoCartao-radioTipo {
  display: none;
}

.opcoesDoCartao-tipo {
  background: currentcolor;
  border-color: rgba(0, 0, 0, 0.5);
  box-sizing: border-box;
}

.opcoesDoCartao-radioTipo:checked + .opcoesDoCartao-tipo {
  background: currentcolor;
  border: 5px solid rgba(0, 0, 0, 0.5);
}

.opcoesDoCartao-opcao {
  pointer-events: none;
  opacity: 0;
  transition: opacity 0.3s;
}

.cartao:hover .opcoesDoCartao-opcao,
.cartao--focado .opcoesDoCartao-opcao {
  opacity: 1;
  pointer-events: auto;
}

@media (min-width: 560px) {
  .cartao {
    flex-grow: 1;
    display: inline-block;
    text-align: left;
    box-sizing: border-box;
    vertical-align: top;
    max-width: 377px;
  }

  .cartao--textoPequeno .cartao-conteudo {
    font-size: 1em;
    width: 11em;
    flex-basis: 11em;
  }

  .cartao--textoMedio .cartao-conteudo {
    font-size: 1.5em;
    width: 9em;
    flex-basis: 9em;
  }

  .cartao--textoGrande .cartao-conteudo {
    font-size: 2em;
    width: 6em;
    flex-basis: 6em;
  }
}
</style>



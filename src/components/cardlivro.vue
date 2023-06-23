<script setup>
import mButton from '@/components/mButton.vue';

import { adicionarAoCarrinho } from '@/_data/carrinho.js';

import CartPlus from 'vue-material-design-icons/CartPlus.vue'

import ShareVariant from 'vue-material-design-icons/ShareVariant.vue'

const props = defineProps ({
    livro: Object
})

function formatarPreco(preco) {
  return 'R$ ' + preco.toFixed(2).replace('.', ',')
}

</script>

<template> 
<div class="card-livro" >
        <div class="card-info-livro">
          <div class="wrap-livro">
            <img :src="props.livro.img" alt="Capa do livro" class="capa-livro" />
          </div>
          <p class="titulo-livro">{{ props.livro.title }}</p>
          <p class="autor-livro">{{ props.livro.author }}</p>
          <p class="preco-livro">{{ formatarPreco(props.livro.price) }}</p>
        </div>
        <div class="card-buttons-livros">
          <m-button class="escuro" @click="adicionarAoCarrinho(props.livro)">
            <cart-plus/> Adicionar ao carrinho
          </m-button>
          <m-button class="claro"> 
            <share-variant /> Compartilhar
          </m-button>
        </div>
      </div>
</template>

<style scoped>

.escuro {
  background-color: #343a40;
}
.escuro:hover {
  background-color: #dae0e5;
}
.claro {
  background-color: #343a40;
}
.claro:hover {
  background-color: #dae0e5;
}
.card-livro {
  margin: 5px 10px;
  padding: 10px;
  background-color: gray;
  border-radius: 10px;
  width: 180px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.wrap-livro {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  border-radius: 10px;
  width: 180px;
  height: 270px;
}
.capa-livro {
  width: 90%;
  max-height: 100%;
}

.card-livro p {
  margin: 0;
}

.card-livro .titulo-livro {
  font-weight: bold;
  margin-bottom: 5px;
}
</style>
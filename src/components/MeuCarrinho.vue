<script setup>
import MMesage from '@/components/MMesage.vue';

import mButton from '@/components/mButton.vue';

import deleteforever from 'vue-material-design-icons/DeleteForever.vue'

import cartoff from 'vue-material-design-icons/CartOff.vue'

import star from 'vue-material-design-icons/Star.vue'

import cartvariant from 'vue-material-design-icons/CartVariant.vue'

import {carrinho, atualizaQuantidadeItem, removerItemCarrinho} from '@/_data/carrinho.js'


function formatarPreco(preco) {
  return 'R$ ' + preco.toFixed(2).replace('.', ',')
}

</script>

<template> 

<div class="carrinho">
      <h2>Meu carrinho</h2>
      <div class="wrap-carrinho">
        <m-mesage v-if="carrinho.itens.length === 0"/>
        <div v-else>
          <div class="item-carrinho" v-for="(item, index) in carrinho.itens" :key="index">
            <div class="info-livro">
              <div class="imagem-livro">
                <img :src="item.img" class="icon-capa-livro" />
              </div>
              <div class="detalhes-livro">
                <div>
                  <p>{{ item.title }}</p>
                  <p class="info-livro-preco">{{ formatarPreco(item.price) }}/un</p>
                </div>
                <div>
                  <p>
                    Quantidade:
                    <input
                      type="number"
                      v-model="item.quantidade"
                      @change="atualizaQuantidadeItem(item)"
                      min="1"
                    />
                  </p>
                  <button @click="removerItemCarrinho(item)">&#128465;</button>
                  <p>Total: {{ formatarPreco(item.total) }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <m-button class="limpar" texto="Limpar"> <deleteforever/> Limpar </m-button>
        <m-button class="fechar" texto="Fechar Carrinho"> <cartoff/> Fechar Carrinho </m-button>
        <m-button class="fav" texto="Favoritos"> <star/> Favoritos </m-button>
        <m-button class="continue" texto="Continar Comprando"> <cartvariant/> Contimuar Comprando </m-button>
        <p class="carrinho-total">Total: {{ formatarPreco(carrinho.total) }}</p>
      </div>
    </div>

</template>

<style scoped>

.wrap-carrinho .carrinho-total {
  position: fixed;
  bottom: 3%;
  font-size: 1.5rem;
  font-weight: bold;
}

.item-carrinho .info-livro {
  display: flex;
  margin-bottom: 10px;
}
.detalhes-livro {
  display: flex;
  flex-direction: column;
  width: 100%;
}
.detalhes-livro p {
  margin: 0;
}
.detalhes-livro div {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.detalhes-livro input[type='number'] {
  width: 50px;
  text-align: center;
  border: none;
  border-bottom: 1px solid black;
  background-color: transparent;
  margin-left: 10px;
}

.detalhes-livro button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  font-size: 1.5rem;
  color: black;
  padding: 0;
  margin: 0;
}

.info-livro-preco {
  margin-left: auto;
}
.icon-capa-livro {
  width: 30px;
  margin-right: 10px;
}

.limpar {
  background-color: #dc3545;
}

.fechar {
  background-color: #c82333;
}

.fav {
  background-color: #ffc107;
}

.continue {
  background-color: #218838;
}

</style>
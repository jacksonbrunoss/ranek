<template>
  <div class="lista-produtos">
    <div class="container">
      <div class="produto" v-for="produto in produtos" :key="produto.id">
        <img
          v-if="produto.fotos"
          :src="produto.fotos[0].src"
          :alt="produto.fotos[0].titulo"
        />
        <p class="preco">{{ produto.preco }}</p>
        <h2 class="titulo">{{ produto.nome }}</h2>
        <p>{{ produto.descricao }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { api } from "@/services/services.js";
export default {
  name: "ProdutosLista",
  data() {
    return {
      produtos: null
    };
  },
  methods: {
    GetProducts() {
      try {
        api.get(`/produto`).then(res => {
          this.produtos = res.data;
        });
      } catch (error) {
        console.log(error);
      }
    }
  },
  created() {
    this.GetProducts();
  }
};
</script>

<style></style>

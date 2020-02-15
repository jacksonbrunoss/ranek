<template>
  <div class="lista-produtos">
    <div class="container">
      <div v-if="produtos" class="content-produtos">
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
  </div>
</template>

<script>
import { api } from "@/services/services.js";
import { serialize } from "@/helpers.js";
export default {
  name: "ProdutosLista",
  data() {
    return {
      produtos: null,
      produtosPorPagina: 9
    };
  },
  computed: {
    url() {
      const query = serialize(this.$route.query);
      return `/produto?_limit=${this.produtosPorPagina}${query}`;
    }
  },
  methods: {
    GetProducts() {
      try {
        api.get(this.url).then(res => {
          this.produtos = res.data;
        });
      } catch (error) {
        console.log(error);
      }
    }
  },
  watch: {
    url() {
      this.GetProducts();
    }
  },
  created() {
    this.GetProducts();
  }
};
</script>

<style></style>

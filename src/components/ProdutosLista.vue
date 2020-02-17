<template>
  <div class="lista-produtos">
    <div class="container">
      <div v-if="produtos && produtos.length" class="content-produtos">
        <div class="produto" v-for="(produto, index) in produtos" :key="index">
          <router-link to="/">
            <img v-if="produto.fotos" :src="produto.fotos[0].src" :alt="produto.fotos[0].titulo" />
            <p class="preco">{{ produto.preco }}</p>
            <h2 class="titulo">{{ produto.nome }}</h2>
            <p>{{ produto.descricao }}</p>
          </router-link>
        </div>
        <ProdutosPaginar :produtosTotal="produtosTotal" :produtosPorPagina="produtosPorPagina" />
      </div>
      <div v-else-if="produtos && produtos.length === 0" class="not">
        <p>Busca sem resultados. Tente buscar outro termo.</p>
      </div>
    </div>
  </div>
</template>

<script>
import ProdutosPaginar from "../components/ProdutosPaginar.vue";
import { api } from "@/services/services.js";
import { serialize } from "@/helpers.js";
export default {
  name: "ProdutosLista",
  components: {
    ProdutosPaginar
  },
  data() {
    return {
      produtos: null,
      produtosPorPagina: 9,
      produtosTotal: 0
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
          this.produtosTotal = Number(res.headers["x-total-count"]);
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

<style scoped>
.lista-produtos {
  width: 100%;
}
.container {
  max-width: 1144px;
  margin: 0 auto;
}
.content-produtos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 30px;
  margin: 30px;
}
.produto {
  box-shadow: 0 4px 8px rgba(30, 60, 90, 0.1);
  padding: 10px;
  background: #fff;
  border-radius: 4px;
  transition: all 0.2s;
}
.produto:hover {
  box-shadow: 0 6px 12px rgba(30, 60, 90, 0.1);
  transform: scale(1.1);
  position: relative;
  z-index: 1;
}
.produto img {
  border-radius: 4px;
  margin-bottom: 20px;
}
.titulo {
  margin-bottom: 10px;
}
.preco {
  color: #87f;
}
.not {
  text-align: center;
}
</style>

<template>
  <section class="produto">
    <div class="container">
      <div v-if="produto" class="produto-box">
        <ul class="fotos" v-if="produto.fotos">
          <li v-for="(foto, index) in produtos.fotos" :key="index">
            <img :src="foto.src" :alt="foto.titulo" />
          </li>
        </ul>
        <div class="info">
          <h1>{{produto.nome}}</h1>
          <p class="preco">{{produto.preco | NumeroPreco}}</p>
          <p class="descricao">{{produto.descricao}}</p>
          <button class="btn" v-if="produto.vendido === 'false'">Comprar</button>
          <button class="btn" v-else disabled>Comprar</button>
        </div>
      </div>
      <PaginaCarregando v-else />
    </div>
  </section>
</template>

<script>
import { api } from "../services/services.js";
export default {
  name: "Produto",
  props: ["id"],
  data() {
    return {
      produto: null
    };
  },
  methods: {
    getProduto() {
      api.get(`/produto/${this.id}`).then(res => {
        this.produto = res.data;
      });
    }
  },
  created() {
    this.getProduto();
  }
};
</script>

<style scoped>
.produto-box {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 30px;
}
.preco {
  color: #e80;
  font-weight: bold;
  font-size: 1.5rem;
  margin-bottom: 40px;
}
.descricao {
  font-size: 1.2rem;
}
.btn {
  margin-top: 60px;
  width: 200px;
}
</style>
<template>
  <div class="lista-produtos">
    <div class="container">
      <div class="produto" v-for="produto in produtos" :key="produto.id">
        <img v-if="produto.fotos" :src="produto.fotos[0].src" :alt="produto.fotos[0].titulo" />
        <p class="preco">{{produto.preco}}</p>
        <h2 class="titulo">{{produto.nome}}</h2>
        <p>{{produto.descricao}}</p>
      </div>
    </div>
  </div>
</template>

<script>
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
        fetch(`http://localhost:3000/produto`)
          .then(response => response.json())
          .then(res => {
            this.produtos = res;
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

<style>
</style>
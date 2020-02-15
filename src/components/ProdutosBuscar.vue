<template>
  <div class="buscar-produtos">
    <div class="container">
      <form>
        <input type="text" name="busca" id="busca" v-model="busca" />
        <input
          type="submit"
          id="lupa"
          value="Buscar"
          @click.prevent="buscarProdutos"
        />
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProdutosBuscar",
  data() {
    return {
      busca: ""
    };
  },
  methods: {
    buscarProdutos() {
      this.$router.push({ query: { q: this.busca } });
    }
  }
};
</script>

<style></style>

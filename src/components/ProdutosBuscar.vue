<template>
  <div class="buscar-produtos">
    <div class="container">
      <form class="form-buscar">
        <input
          type="text"
          name="busca"
          class="buscar"
          placeholder="Buscar produto..."
          v-model="busca"
        />
        <input
          type="submit"
          class="lupa"
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

<style scoped>
.form-buscar {
  max-width: 600px;
  margin: 30px auto 60px auto;
  position: relative;
}
.buscar {
  width: 100%;
  box-shadow: 0 4px 8px rgba(30, 60, 90, 0.1);
  padding: 20px;
  border: none;
  border-radius: 4px;
  transition: all 0.2s;
}
.buscar:focus,
.buscar:hover {
  outline: none;
  transform: scale(1.1);
  box-shadow: 0 6px 12px rgba(30, 60, 90, 0.2);
}
.lupa {
  width: 62px;
  height: 62px;
  background: url("../assets/search.svg") no-repeat center center;
  text-indent: -150px;
  border: none;
  cursor: pointer;
  position: absolute;
  top: 0px;
  right: 0px;
  box-shadow: none;
}
</style>

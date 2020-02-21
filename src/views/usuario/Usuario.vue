<template>
  <section class="container">
    <nav class="sidbar">
      <ul>
        <li>
          <router-link :to="{name: 'usuario'}">Produtos</router-link>
        </li>
        <li>
          <router-link :to="{name: 'compras'}">Compras</router-link>
        </li>
        <li>
          <router-link :to="{name: 'vendas'}">Vendas</router-link>
        </li>
        <li>
          <router-link :to="{name: 'usuario-editar'}">Editar usuario</router-link>
        </li>
        <li>
          <button class="btn" @click.prevent="deslogar">Deslogar</button>
        </li>
      </ul>
    </nav>
    <transition mode="out-in">
      <router-view />
    </transition>
  </section>
</template>

<script>
export default {
  name: "Usuario",
  methods: {
    deslogar() {
      this.$store.dispatch("deslogarUsuario");
      this.$router.push("/login");
    }
  }
};
</script>

<style>
</style>
<template>
  <section class="usuarioForm">
    <form class="usuario-form">
      <label for="nome">Nome</label>
      <input type="name" name="nome" v-model="nome" />
      <label for="email">Email</label>
      <input type="email" name="email" v-model="email" />
      <label for="senha">Senha</label>
      <input type="password" name="senha" v-model="senha" />
      <label for="cep">Cep</label>
      <input type="text" name="cep" v-model="cep" />
      <label for="rua">Rua</label>
      <input type="text" name="rua" v-model="rua" />
      <label for="numero">Numero</label>
      <input type="text" name="numero" v-model="numero" />
      <label for="bairro">Bairro</label>
      <input type="text" name="bairro" v-model="bairro" />
      <label for="cidade">Cidade</label>
      <input type="text" name="cidade" v-model="cidade" />
      <label for="estado">Estado</label>
      <input type="text" name="estado" v-model="estado" />
      <div class="button">
        <slot></slot>
      </div>
    </form>
  </section>
</template>

<script>
import { mapFields } from "@/helpers.js";
export default {
  name: "UsuarioForm",
  computed: {
    ...mapFields({
      fields: [
        "nome",
        "email",
        "senha",
        "rua",
        "cep",
        "numero",
        "bairro",
        "cidade",
        "estado"
      ],
      base: "usuario",
      mutation: "UPDATE_USUARIO"
    })
  }
};
</script>

<style scoped>
.usuario-form {
  display: grid;
  grid-template-columns: 80px 1fr;
  align-items: center;
}
.button {
  grid-column: 2;
  margin-top: 10px;
}
</style>
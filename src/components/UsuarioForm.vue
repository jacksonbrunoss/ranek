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
      <input type="text" name="cep" v-model="cep" @keyup="preencherCep" />
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
import { getCep } from "@/services/services.js";
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
  },
  methods: {
    preencherCep() {
      const cep = this.cep.replace(/\D/g, "");
      if (cep.length === 8) {
        getCep(cep).then(response => {
          this.rua = response.data.logradouro;
          this.bairro = response.data.bairro;
          this.estado = response.data.uf;
          this.cidade = response.data.localidade;
        });
      }
    }
  }
};
</script>

<style scoped>
.usuario-form {
  max-width: 500px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 80px 1fr;
  align-items: center;
}
.button {
  grid-column: 2;
  margin-top: 10px;
}
</style>
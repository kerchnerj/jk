<script>
import AutoresApi from "@/api/autores.js";
const autoresApi = new AutoresApi();
export default {
  data() {
    return {
      autor: {},
      autores: [],
    };
  },
  async created() {
    this.autores = await autoresApi.buscarTodosOsAutores();
  },
  methods: {
    async salvar() {
      if (this.autor.id) {
        await autoresApi.atualizarAutor(this.autor);
      } else {
        await autoresApi.adicionarAutor(this.autor);
      }
      this.autores = await autoresApi.buscarTodosOsAutores();
      this.autor = {};
    },
    async excluir(autor) {
      await autoresApi.excluirAutor(autor.id);
      this.autores = await autoresApi.buscarTodosOsAutores();
    },
    editar(autor) {
      Object.assign(this.autor, autor);
    },
  },
};
</script>
<template>
  <main>
    <div class="container">
      <div class="title">
        <h1>Gerenciamento de autores</h1>
      </div>
      <div class="form-input">
        <input
          type="text"
          v-model="autor.nome"
          @keyup.enter="salvar"
          placeholder="Autor..."
        />
        <button @click="salvar">Salvar</button>
      </div>
      <div class="list-livros">
        <table v-if="autores.length > 0">
          <thead>
            <tr>
              <th>ID</th>
              <th>Autor</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="autor in autores" :key="autor.id">
              <td>{{ autor.id }}</td>
              <td>{{ autor.nome }}</td>
              <td>
                <button @click="editar(autor)">editar</button>
                <button @click="excluir(autor)">excluir</button>
              </td>
            </tr>
          </tbody>
        </table>
        <div class="senao" v-else>
          <span class="aviso">Não existem autores cadastrados</span>
        </div>
      </div>
    </div>
  </main>
</template>
<style>
.title {
  display: flex;
  justify-content: center;
  margin-top: 30px;
     font-family:Georgia, 'Times New Roman', Times, serif;
}
.form-input {
  margin-top: 10px;
  display: flex;
  justify-content: center;
}
.form-input input {
  width: 60%;
  height: 40px;
  border: 1px solid rgb(147, 147, 147);
  border-radius: 10px;
  padding: 0 10px;
}
.form-input button {
  margin-left: 1px;
  width: 20%;
  height: 40px;
  border: 1px solid rgb(211, 211, 211);
  border-radius: 10px;
  background-color: rgba(67,61,61,0.65);
  color: rgb(255, 255, 255);
  font-weight: bold;
  cursor: pointer;
}
.list-autores {
  display: flex;
  justify-content: center;
}
.list-autores table {
  width: 80%;
  margin: 0 auto;
  border-collapse: collapse;
}
table tr td {
  border: 1px solid rgb(211, 211, 211);
  padding: 10px;
}
</style>
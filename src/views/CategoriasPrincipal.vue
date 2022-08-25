<script>
import CategoriasApi from "@/api/categorias.js";
const categoriasApi = new CategoriasApi();
export default {
  data() {
    return {
      categoria: {},
      categorias: [],
    };
  },
  async created() {
    this.categorias = await categoriasApi.buscarTodasAsCategorias();
  },
  methods: {
    async salvar() {
      if (this.categoria.id) {
        await categoriasApi.atualizarCategoria(this.categoria);
      } else {
        await categoriasApi.adicionarCategoria(this.categoria);
      }
      this.categorias = await categoriasApi.buscarTodasAsCategorias();
      this.categoria = {};
    },
    async excluir(categoria) {
      await categoriasApi.excluirCategoria(categoria.id);
      this.categorias = await categoriasApi.buscarTodasAsCategorias();
    },
    editar(categoria) {
      Object.assign(this.categoria, categoria);
    },
  },
};
</script>
<template>
  <main>
    <div class="container">
      <div class="title">
        <h1>Gerenciamento de categorias</h1>
      </div>
      <div class="form-input">
        <input
          type="text"
          v-model="categoria.descricao"
          placeholder="Categoria..."
        />
        <button @click="salvar">Salvar</button>
      </div>
      <div class="list-categorias">
        <table v-if="categorias.length > 0">
          <thead>
            <tr>
              <th>ID</th>
              <th>Categoria</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="categoria in categorias" :key="categoria.id">
              <td>{{ categoria.id }}</td>
              <td>{{ categoria.descricao }}</td>
              <td>
                <button @click="editar(categoria)">editar</button>
                <button @click="excluir(categoria)">excluir</button>
              </td>
            </tr>
          </tbody>
        </table>
        <div class="senao" v-else>
          <span class="aviso">Não existem categorias cadastradas</span>
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
  border: 1px solid rgb(0, 0, 0);
  border-radius: 10px;
  background-color: rgba(67,61,61,0.65);
  color: white;
  font-weight: bold;
  cursor: pointer;
}
.list-categorias{
  margin-top: 15px;
  display: flex;
  justify-content: center;
}
.list-categorias table{
  width: 80%;
  margin: 0 auto;
  border-collapse: collapse;
}
table tr td{
  border: 1px solid rgb(0, 0, 0);
  padding: 10px;
}
</style>
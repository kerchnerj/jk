<script>
import LivrosApi from "@/api/livros.js";
import AutoresApi from "@/api/autores.js";
import CategoriasApi from "@/api/categorias.js";
import EditorasApi from "@/api/editoras.js";
const livrosApi = new LivrosApi();
const autoresApi = new AutoresApi();
const categoriasApi = new CategoriasApi();
const editorasApi = new EditorasApi();
export default {
  data() {
    return {
      livro: {},
      livros: [],
      categoria: {},
      categorias: [],
      editora: {},
      editoras: [],
      autor: {},
      autores: [],
    };
  },
  async created() {
    this.livros = await livrosApi.buscarTodosOsLivros();
    this.autores = await autoresApi.buscarTodosOsAutores();
    this.categorias = await categoriasApi.buscarTodasAsCategorias();
    this.editoras = await editorasApi.buscarTodasAsEditoras();
  },
  methods: {
    async salvar() {
      if (this.livro.id) {
        await livrosApi.atualizarLivro(this.livro);
      } else {
        await livrosApi.adicionarLivro(this.livro);
      }
      this.livros = await livrosApi.buscarTodosOsLivros();
      this.categorias = await categoriasApi.buscarTodasAsCategorias();
      this.editoras = await editorasApi.buscarTodasAsEditoras();
      this.autores = await autoresApi.buscarTodosOsAutores();
      this.livro = {};
    },
    async excluir(livro) {
      await livrosApi.excluirLivro(livro.id);
      this.livros = await livrosApi.buscarTodosOsLivros();
    },
    editar(livro) {
      Object.assign(this.livro, livro);
    },
  },
};
</script>

<template>
  <main>
    <div class="container">
      <div class="title">
        <h1>Gerenciamento de livros</h1>
      </div>
      <div class="form-input">
        <div class="center_input">
          <input
            id="input_tit"
            type="text"
            v-model="livro.nome"
            placeholder="Título"
          />
          <select id="categorias" v-model="livro.categoria">
            <option disabled value="">Escolha uma categoria</option>
            <option
              v-for="categoria of categorias"
              :key="categoria.id"
              :value="categoria.descricao"
            >
              {{ categoria.descricao }}
            </option>
          </select>
          <select id="autores" v-model="livro.autor">
            <option disabled value="">Escolha um autor</option>
            <option
              v-for="autor of autores"
              :key="autor.id"
              :value="autor.nome"
            >
              {{ autor.nome }}
            </option>
          </select>
          <select id="editoras" v-model="livro.editora">
            <option disabled value="">Escolha uma editora</option>
            <option
              v-for="editora of editoras"
              :key="editora.id"
              :value="editora.nome"
            >
              {{ editora.nome }}
            </option>
          </select>
          <input
            id="input_quant"
            type="number"
            v-model="livro.quantidade"
            placeholder="Quantidade"
          />
          <input
            id="input_pre"
            type="number"
            v-model="livro.preco"
            placeholder="Preço"
          />
          <div class="center">
            <button @click="salvar">Salvar</button>
          </div>
        </div>
      </div>
      <div class="list-livros">
        <table v-if="livros.length > 0">
          <thead>
            <tr>
              <th>ID</th>
              <th>Título</th>
              <th>Categoria</th>
              <th>Editora</th>
              <th>Autor</th>
              <th>Quantidade</th>
              <th>Preço</th>
              <th>Ação</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="livro in livros" :key="livro.id">
              <td>{{ livro.id }}</td>
              <td>{{ livro.nome }}</td>
              <td>{{ livro.categoria }}</td>
              <td>{{ livro.editora }}</td>
              <td>{{ livro.autor }}</td>
              <td>{{ livro.quantidade }}</td>
              <td>{{ livro.preco }}</td>
              <td>
                <button @click="editar(livro)">editar</button>
                <button @click="excluir(livro)">excluir</button>
              </td>
            </tr>
          </tbody>
        </table>
        <div class="senao" v-else>
          <span class="aviso">Não existem livros cadastrados</span>
          <i class="bx bx-error"></i>
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
   background-color: rgba(67, 61, 61, 0.65);
   color: rgb(255, 255, 255);
   font-weight: bold;
   cursor: pointer;
   font-family: 'IM Fell French Canon SC', serif;
 }
 
 .list-livros {
   display: flex;
   justify-content: center;
 }
 
 .list-livros table {
   width: 80%;
   margin: 0 auto;
   border-collapse: collapse;
 }
 
 table tr td {
   border: 1px solid rgb(211, 211, 211);
   padding: 10px;
 }
 </style>

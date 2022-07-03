<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      editoras: [
        {
          id: "01986caa-0a42-4eef-9d11-25c77fd98df1",
          editoras: "Editora Rocco",
        },
        {
          id: "19be6257-67d9-413a-a0ff-840a8acaba75",
          editoras: "Editora Sextante",
        },
        {
          id: "520465a6-36e2-4554-9499-d2ed6209b9e7",
          editoras: "Panda Books",
        },
        {
          id: "632a0b5e-41f2-4acb-8c36-019b10f81ade",
          editoras: "Companhia das Letras",
        },
        {
          id: "9db7a2ed-e1c2-43b2-b222-47a64a860427",
          editoras: "Editora Arqueiro",
        },
      ],
      novo_editoras: "",
    };
  },
  methods: {
    salvar() {
      const novo_id = (uuidv4);
      this.editoras.push({
        id: novo_id,
        editoras: this.novo_editoras,
      });
    },
  },
};
</script>

<template>
<main>
    <div class="container">
      <div class="title">
        <h2>Gerenciamento de Editoras</h2>
      </div>
      <div class="form-input">
        <input type="text" v-model="novo_editoras" />
        <button @click="salvar"> Salvar </button>
      </div>
      <div class="list-editoras">
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Editoras</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="editoras in editoras" :key="editoras.id">
              <td>{{ editoras.id }}</td>
              <td>{{ editoras.nome }}</td>
            </tr>
          </tbody>
        </table>
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
  background-color:rgba(67,61,61,0.65);
  color: rgb(255, 255, 255);
  font-weight: bold;
  cursor: pointer;
}
.list-editoras{
  display: flex;
  justify-content: center;
}
.list-editoras table{
  width: 80%;
  margin: 0 auto;
  border-collapse: collapse;
}
table tr td{
  border: 1px solid rgb(211, 211, 211);
  padding: 10px;
}
</style>
<template>
<main>
    <div class="container">
      <div class="title">
        <h2>Gerenciamento de Editoras</h2>
      </div>
      <div class="form-input">
        <input type="text" v-model="novo_editora" />
        <button @click="salvar"> Salvar </button>
      </div>
      <div class="list-editoras">
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Editoras</th>
              <th></th>
              <th></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="editoras in editoras" :key="editoras.id">
              <td>{{ editoras.id }}</td>
              <td>{{ editoras.nome }}</td>
              <td>??</td>
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
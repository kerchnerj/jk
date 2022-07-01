<template>
    <main>
        <div class="container">
            <div class="title">
                <h2>Gerenciamento de Livros</h2>
            </div>
            <div class="form-input">
                <input type="text" v-model="novo_livro" />
                <button @click="salvar">Salvar</button>
            </div>
            <div class="list-livros">
                <table>
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Nome</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="livros in livros" :key="livros.id">
                            <td>{{ livros.id }}</td>
                            <td>{{ livros.nome }}</td>
                            <td></td>
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
.list-livros{
  display: flex;
  justify-content: center;
}
.list-livros table{
  width: 80%;
  margin: 0 auto;
  border-collapse: collapse;
}
table tr td{
  border: 1px solid rgb(211, 211, 211);
  padding: 10px;
}
</style>

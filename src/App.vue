<script setup>
import { RouterLink, RouterView } from 'vue-router';

</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Categorias</RouterLink>
        <RouterLink to="/Livros">Livros</RouterLink>
        <RouterLink to="/Editoras">Editoras</RouterLink>
        <RouterLink to="/Autores">Autores</RouterLink>
      </nav>
      <div class="icon">
        <i class='bx bx-log-in'></i>
      </div>
    </div>
  </header>

  <RouterView />
</template>


<style>
@import '@/assets/style.css';
header{
  height: 30px;
  background-color: white;
  padding: 25px;
}
.icon {
  float: right;
  font-size: 30px;

}
a {
  margin-right: 15px;
  text-decoration: none;
  font-size: 26px;
  color: black;
}
a:hover{
  text-decoration: underline;
}
body {
  margin: 0;
  padding: 0;
}
</style>

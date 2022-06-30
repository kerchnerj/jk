<script>
import { RouterLink, RouterView } from 'vue-router';
import MenuLateral from "./components/MenuLateral.vue"
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/Categorias"> Categorias</RouterLink>
        <RouterLink to="/Livros"> Livros </RouterLink>
        <RouterLink to="/Editoras"> Editoras </RouterLink>
        <RouterLink to="/Autores"> Autores </RouterLink>
      </nav>
    </div>
  </header>
  <MenuLateral />

  <RouterView />
</template>

<style>
@import '@/assets/style.css';
</style>

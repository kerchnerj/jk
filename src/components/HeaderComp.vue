<script>
export default{}
</script>
<template>
  <header>
    <div class="menu-esquerdo">
      <span>|</span>
      <span>
        <RouterLink to="/Categorias">Categorias</RouterLink>
      </span>
      <span>|</span>
      <span>
        <RouterLink to="/Livros">Livros</RouterLink>
      </span>
      <span>|</span>
      <span>
        <RouterLink to="/Editoras">Editoras</RouterLink>
      </span>
      <span>|</span>
      <span>
        <RouterLink to="/Autores">Autores</RouterLink>
      </span>
    </div>
    <div class="menu-direito">
      <span>Sair</span>
    </div>
  </header>
</template>

<style>
header span {
  padding: 0 20px;
}

header {
  background-color: rgba(67, 61, 61, 0.65);
  height: 15%;
  font-size: 1.3rem;
  padding-left: 2rem;
  color: white;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
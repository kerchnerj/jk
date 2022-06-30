<script>
export default {}
</script>

<template>
<main>
    <div class="wrapper">
        <nav id="sidebar">
            <div class="sidebar-header">
                <ul>
                    <li>
                        <RouterLink>
                            <i class='bx bx-book-alt'></i>
                            <span>Livros</span>
                        </RouterLink>
                    </li>
                    <li>
                        <RouterLink>
                            <i class='bx bxs-book-reader'></i>
                            <span> Autores </span>
                        </RouterLink>
                    </li>
                         <li>
                             <RouterLink>
                                 <i class='bx bx-comment-edit'></i>
                                 <span> Editoras </span>
                             </RouterLink>
                        </li>
                        <li>
                            <RouterLink>
                                <i class='bx bxs-category-alt'></i>
                                <span> Categorias </span>
                            </RouterLink>
                        </li>
                </ul>
            </div>
        </nav>
    </div>
</main>
</template>
<template>
  <form class="searchBar">
    <label for="categoryName">Busca una categoria</label>
    <input
      class="searchBar-input"
      name="categoryName"
      type="text"
      placeholder="Buscar..."
    />
  </form>
</template>

<script>
export default {};
</script>

<style>
.searchBar {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem;
}

.searchBar-input {
  border: 1px solid #5931c9;
  border-radius: 1rem;
  padding: 0.5rem;
}
</style>

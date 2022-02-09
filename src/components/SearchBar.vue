<template>
  <div class="searchBar" @keyup.prevent="onSearchCategory">
    <label for="categoryName">Busca una categoria</label>
    <input
      class="searchBar-input"
      name="categoryName"
      type="text"
      v-model="categoryName"
      placeholder="Buscar..."
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      categoryName: "",
    };
  },
  methods: {
    onSearchCategory() {
      this.$emit("category-search", this.categoryName);
    },
  },
};
</script>

<style>
.searchBar {
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  padding: 2rem;
}

.searchBar > label {
  margin-bottom: 12px;
}

.searchBar-input {
  border: 1px solid #5931c9;
  border-radius: 1rem;
  padding: 0.5rem;
  outline: none;
}
.searchBar-input[type=text]:focus {
  box-shadow: 0 0 5px #5931c9;
  border: 1px solid #5931c9;
}
</style>

<template>
  <!-- <div class="categoryList_notFound" v-if="categoryList">
      <h2>No se encuentran categorias</h2>
    </div> -->
  <div>
    <div v-if="isLoading" class="loader-container">
      <img
        class="loader"
        src="https://cssbud.com/wp-content/uploads/2021/08/tweaking-robot.gif"
        alt="Loader"
      />
    </div>
    <main class="categoryList">
      <category
        v-for="category in categoryList"
        :key="category.uuid4"
        :id="category.uuid4"
        :name="category.name"
        :category_type="category.category_type"
        :price="category.suggested_budget"
        :image="category.image"
      >
      </category>
    </main>
  </div>
</template>

<script>
import Category from "./Category.vue";

export default {
  components: { Category },
  props: ["categoryList", "isLoading"],
};
</script>

<style>
.categoryList {
  display: grid;
  gap: 0.5rem;
  grid-auto-rows: 9rem;
  grid-template-columns: repeat(auto-fill, minmax(15rem, 1fr));
  padding: 1.2rem;
}
.categoryList_notFound {
  text-align: center;
}
.loader-container {
  display: flex;
  justify-content: center;
}

.loader {
  width: 30%;
}
</style>

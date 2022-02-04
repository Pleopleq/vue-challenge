<template>
  <main class="categoryList">
    <!-- <div class="categoryList_notFound" v-if="categoryList">
      <h2>No se encuentran categorias</h2>
    </div> -->
    <div v-if="isLoading" class="loader-container">
      <img
        class="loader"
        src="https://cssbud.com/wp-content/uploads/2021/08/tweaking-robot.gif"
        alt="Loader"
      />
    </div>
    <category v-for="category in categoryList" :key="category.id"> </category>
  </main>
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
  padding: 2rem;
  background-color: antiquewhite;
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

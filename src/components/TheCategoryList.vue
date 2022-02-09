<template>
  <div>
    <div v-if="isLoading" class="loader-container">
      <img
        class="loader"
        src="https://cssbud.com/wp-content/uploads/2021/08/tweaking-robot.gif"
        alt="Loader"
      />
    </div>
    <div class="categoryList_notFound" 
      v-if="(isCategoryListEmpty && !isLoading) || (isError && !isLoading)"
    >
      <h2>{{feedbackMsg}}</h2>
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
  props: ["categoryList", "isLoading", "isError"],
  computed: {
    isCategoryListEmpty() {
      if (this.categoryList.length === 0) {
        return true;
      }
      return false;
    },
    feedbackMsg() {
      if(this.isCategoryListEmpty && !this.isLoading && !this.isError) { 
        return "No se encuentran categorias :("
      }
      if(this.isError && !this.isLoading){
        return 'Algo salio mal. Intenta mas tarde!'
      }
      return null
    }
  },
};
</script>

<style>
.categoryList {
  display: grid;
  gap: 0.5rem;
  grid-auto-rows: 11rem;
  grid-template-columns: repeat(auto-fill, minmax(19rem, 1fr));
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

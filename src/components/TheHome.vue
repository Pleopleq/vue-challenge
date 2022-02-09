<template>
  <div>
    <search-bar @category-search="onCategorySearch"></search-bar>
    <the-category-list
      :categoryList="categoryList"
      :isLoading="isLoading"
      :isError="isError"
    ></the-category-list>
  </div>
</template>

<script>
import SearchBar from "./SearchBar.vue";
import TheCategoryList from "./TheCategoryList.vue";
export default {
  components: {
    SearchBar,
    TheCategoryList,
  },
  data() {
    return {
      categoryList: [],
      resetList: [],
      categorySearch: "",
      isLoading: false,
      isError: false,
    };
  },
  methods: {
    getCategories() {
      this.isLoading = true;
      this.isError = false;
      fetch("https://apitesting.plerk.io/v2/category", {
        method: "GET",
        headers: {
          "Content-Type": "application/json",
          Authorization: process.env.VUE_APP_API_KEY,
        },
      })
        .then((response) => response.json())
        .then((data) => {
          this.isLoading = false;
          this.categoryList = data.data;
          this.resetList = data.data;
        })
        .catch((error) => {
          this.isLoading = false;
          this.isError = true;
          console.error(error);
        });
    },
    onCategorySearch(categoryName) {
      this.resetCategories();
      this.categoryList = this.categoryList.filter((item) => {
        return item.name.esp.toLowerCase().includes(categoryName);
      });
    },
    resetCategories() {
      this.categoryList = this.resetList;
    },
  },
  created() {
    this.getCategories();
  },
};
</script>

<style></style>

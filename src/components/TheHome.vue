<template>
  <div>
    <search-bar @category-search="onCategorySearch"></search-bar>
    <the-category-list
      :categoryList="categoryList"
      :isLoading="isLoading"
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
    };
  },
  methods: {
    getCategories() {
      this.isLoading = true;
      fetch("https://apitesting.plerk.io/v2/category", {
        method: "GET",
        headers: {
          'Access-Control-Allow-Origin': 'fervent-saha-9bf285.netlify.app',
          "Content-Type": "application/json",
          Authorization:
            "Bearer " +
            "5bc95bf034d900548243a59e2296bd683729bd75057879fd0f877d3adc7d1db6bedbfccb47aca04e44ef28adf4c3e9e72afe2f2b295b3bf08e2a47ec75f9607d",
        },
      })
        .then((response) => response.json())
        .then((data) => {
          this.isLoading = false;
          this.categoryList = data.data;
          this.resetList = data.data;
        })
        .catch((error) => console.error(error));
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

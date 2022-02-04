<template>
  <div class="category-container">
    <div class="category-image">
      <img :src="image" alt="" />
    </div>
    <div class="category-body">
      <p>{{ name.esp }}</p>
      <p>Precio: {{ priceToUSD }}</p>
      <p>Tipo: {{ categoryType }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["id", "name", "category_type", "description", "price", "image"],
  computed: {
    categoryType() {
      if (this.category_type === 1) {
        return "Normal";
      }
      if (this.category_type === 2) {
        return "Libre";
      }
      return "Personalizada";
    },
    priceToUSD() {
      const dollars = this.price / 100;
      return dollars.toLocaleString("en-US", {
        style: "currency",
        currency: "USD",
      });
    },
  },
};
</script>

<style>
.category-container {
  display: flex;
  border: 1px solid #5931c9;
}

.category-image {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 6rem;
}

.category-image > img {
  width: 5rem;
}

.category-body {
  padding-left: 1rem;
}
</style>

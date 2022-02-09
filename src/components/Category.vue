<template>
  <base-card>
    <div class="category-image">
      <img :src="checkImage" alt="" />
    </div>
    <div class="category-body">
      <h3>{{ name.esp }}</h3>
      <p>Precio: {{ priceToUSD }} USD</p>
      <p>Tipo: {{ categoryType }}</p>
    </div>
  </base-card>
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
    checkImage() {
      if(this.image.split('/').length > 6) {
        const realURL = this.image.split('/').splice(4, this.image.length).join('/')
        return realURL
      }
      return this.image
    }
  },
};
</script>

<style>
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
  padding-right: 1rem;
}
</style>

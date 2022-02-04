<template>
    <article class="category-container">
        <slot></slot>
    </article>
</template>

<script>
export default {

}
</script>

<style>
.category-container {
  display: flex;
  border: 1px solid #5931c9;
  border-radius: 12px;
  box-shadow: 0 0 3px #5931c9;
}
</style>
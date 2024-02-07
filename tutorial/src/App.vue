<script setup>
const count = 10;
const shoppingList = ["Apple", "Meat", "Pencils"]
</script>

<template>
  <div>
    <h1>Hello World !</h1>
    <p v-if="count < 10">⏬ Less than 10</p>
    <p v-else-if="count === 10">⏩ Equal 10</p>
    <p v-else>⏫ More than 10</p>
    <span v-for="item in shoppingList"> {{ item }}</span>
  </div>

</template>

<style scoped>
div {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
h1 {
  color: green;
  font-style: oblique;
}
</style>

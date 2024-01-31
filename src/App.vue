<script setup>
import MyCounter from "@/components/MyCounter.vue";
import {ref} from "vue";

const count = ref(0);
</script>

<template>
  <div class="app">
    <h1>Vue 3 Composition API</h1>
    <p>Count is: {{ count }}</p>
    <my-counter v-model="count" />
    <p v-if="count < 10">⏬ 10</p>
    <p v-else-if="count === 10">⏩ 10</p>
    <p v-else-if="count > 10">⏫ 10</p>
  </div>
</template>


<style scoped>
  .app {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1rem;
}
</style>

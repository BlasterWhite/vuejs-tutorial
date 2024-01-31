<script setup>
import {ref} from "vue";

const emits = defineEmits(["increment"]);

const props = defineProps({
  modelValue: {
    type: Number,
    required: true,
  },
})

const count = ref(props.modelValue);

function increment() {
  count.value++;
  emits("update:modelValue", count.value);
}
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>

<style scoped>
  button {
  background-color: #eee;
  border: none;
  border-radius: 4px;
  color: #333;
  font-size: 1.5em;
  padding: 0.5em 1em;
}
</style>
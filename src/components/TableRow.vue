<script setup>
import {computed} from 'vue'

const props = defineProps({
  row: {
    type: Object,
    required: true,
  },
});

const rowComputed = computed({
  get() {
    return props.row;
  },
  set(value) {
    emit('update:row', value);
  },
});

const emit = defineEmits(['update:row', 'delete:row']);
</script>

<template>
  <tr>
    <td>{{ rowComputed.id }}</td>
    <td>
      <input
        type="text"
        :value="rowComputed.text"
        @input="rowComputed.text = $event.target.value"
      />
    </td>
    <td>
      <input
        type="checkbox"
        :checked="rowComputed.done"
        @change="rowComputed.done = $event.target.checked"
      />
      <button
        @click="emit('delete:row', rowComputed)"
      > Delete
      </button>
    </td>
  </tr>
</template>

<style scoped>
input[type='checkbox'] {
  width: 20px;
  height: 20px;
}

input[type='text'] {
  font-family: sans-serif;
  background: transparent;
  color: #fff;
  border: none;
  border-bottom: 1px solid #28f8ea;
}

input[type='text']:focus {
  outline: none;
  border-bottom: 1px solid #f8285f;
}
</style>
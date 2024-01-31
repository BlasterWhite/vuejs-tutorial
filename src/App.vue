<script setup>
import {computed, ref} from 'vue'
import TableRow from "@/components/TableRow.vue";

const list = ref([
  {id: 1, text: 'Groceries', done: true},
  {id: 2, text: 'Laundry', done: false},
  {id: 3, text: 'Dishes', done: false},
]);

const addTodo = () => {
  list.value.push({
    id: list.value[list.value.length - 1].id + 1,
    text: 'New task',
    done: false,
  });
};

const deleteRow = (row) => {
  list.value = list.value.filter((item) => item.id !== row.id);
};

const numberOfTodos = computed(() => {
  return list.value.map((item) => !item.done).filter((item) => item).length;
});
</script>

<template>
  <div class="app">
    <h1>Todo List</h1>
    <p>{{ numberOfTodos }} task(s) left</p>
    <table>
      <thead>
      <tr>
        <th>Number</th>
        <th>Task</th>
        <th>Actions</th>
      </tr>
      </thead>
      <tbody>
        <table-row v-for="item in list" :key="item.id" :row="item" @delete:row="deleteRow" />
      </tbody>
    </table>
    <button @click="addTodo">Add Todo</button>
  </div>
</template>

<style scoped>
.app {
  font-family: sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

button {
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  border: none;
  background: #499322;
  color: #fff;
  font-weight: bold;
  cursor: pointer;
}
</style>

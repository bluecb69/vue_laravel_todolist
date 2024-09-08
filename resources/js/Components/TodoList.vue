<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const todos = ref([]);
const newTodo = ref('');

const fetchTodos = async () => {
  try {
    const response = await axios.get('/api/todos');
    todos.value = response.data;
  } catch (error) {
    console.error('獲取待辦事項時發生錯誤:', error);
  }
};

const addTodo = async () => {
  if (newTodo.value.trim()) {
    try {
      const response = await axios.post('/api/todos', { title: newTodo.value });
      todos.value.push(response.data);
      newTodo.value = '';
    } catch (error) {
      console.error('新增待辦事項時發生錯誤:', error);
    }
  }
};

const removeTodo = async (id) => {
  try {
    await axios.delete(`/api/todos/${id}`);
    todos.value = todos.value.filter(todo => todo.id !== id);
  } catch (error) {
    console.error('刪除待辦事項時發生錯誤:', error);
  }
};

onMounted(fetchTodos);
</script>

<template>
  <div class="space-y-4 bg-gray-100 p-6 rounded-lg">
    <div class="mb-4">
      <input
        v-model="newTodo"
        @keyup.enter="addTodo"
        placeholder="新增待辦事項"
        class="w-full p-3 bg-white border-2 border-teal-400 rounded-lg focus:outline-none focus:border-teal-500 text-gray-800 placeholder-gray-400 shadow-sm"
      >
    </div>
    <ul class="space-y-2">
      <li
        v-for="todo in todos"
        :key="todo.id"
        class="flex items-center bg-white p-4 rounded-lg border-l-4 border-teal-400 shadow-sm transition duration-200 ease-in-out hover:shadow-md"
      >
        <input
          type="checkbox"
          v-model="todo.completed"
          class="mr-4 form-checkbox h-5 w-5 text-teal-500 rounded focus:ring-teal-400 focus:ring-offset-white"
        >
        <span
          :class="{ 'line-through text-gray-400': todo.completed, 'text-gray-800': !todo.completed }"
          class="flex-grow"
        >
          {{ todo.title }}
        </span>
        <button
          type="button"
          @click="removeTodo(todo.id)"
          class="ml-4 bg-red-400 hover:bg-red-500 text-white px-3 py-1 rounded-md transition duration-200 ease-in-out"
        >
          刪除
        </button>
      </li>
    </ul>
  </div>
</template>

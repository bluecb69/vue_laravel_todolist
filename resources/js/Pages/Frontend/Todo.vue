<script setup>
import { defineOptions } from 'vue';
import TodoList from '@/Components/TodoList.vue';

defineOptions({
  layout: null,
});
</script>

<template>
  <div class="min-h-screen bg-gradient-to-br from-teal-100 to-gray-200 text-gray-800 p-4 sm:p-8">
    <div class="max-w-2xl mx-auto bg-white rounded-lg shadow-lg p-6 sm:p-8">
      <h1 class="text-3xl font-bold mb-6 text-teal-600 text-center">待辦事項列表</h1>
      <TodoList />
    </div>
  </div>
</template>

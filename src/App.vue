<script setup>
import AddTodoForm from './components/AddTodoForm.vue'
import TodoItem from './components/TodoItem.vue'
import {ref} from 'vue';

const todoList = ref([]);

const addNewTodo = (newTodo) => {
  todoList.value.push({
    complete:false,
    text:newTodo,
  });
}

const deleteTodoItem = index => {
  todoList.value.splice(index,1);
}

</script>

<template>
  <div class="min-h-screen w-100 bg-slate-900">
    <div class="max-w-3xl py-6 px-4 mx-auto">
      <div class="text-center my-6">
        <h1 class="text-3xl text-white font-semibold">Todo List</h1>
      </div>

      <div class="bg-slate-800 rounded-lg shadow-sm divide-y divide-gray-700">
        <AddTodoForm @addNewTodo="addNewTodo"></AddTodoForm>

        <div v-if='todoList.length > 0' class="divide-y divide-gray-700">
          <TodoItem v-for="(item,index) in todoList" @deleteItem='deleteTodoItem(index)' :key='index' :item="item"></TodoItem>
        </div>
      </div>
    </div>
  </div>
</template>

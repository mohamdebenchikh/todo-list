<template>
  <form @submit.prevent="submit">
    <div class="px-3 py-4 flex gap-2 items-center">
      <input
        class="w-full bg-transparent border border-gray-600 ring-2 ring-transparent ring-offset-2 ring-offset-slate-800 focus:ring-indigo-500 px-4 py-2 rounded-md outline-none text-white"
        placeholder="Enter your todo"
        v-model='newTodo'
      />
      <button type='submit' class="uppercase px-3 py-2 bg-slate-900 text-white rounded-md">
        Add
      </button>
    </div>
  </form>
</template>
<script setup>
import {ref} from 'vue';

const newTodo = ref('');

const emits = defineEmits(['addNewTodo']);

const submit = ()  => {
    emits('addNewTodo',newTodo.value);
    newTodo.value = "";
}

</script>

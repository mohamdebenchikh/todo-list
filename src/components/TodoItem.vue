<template>
  <div class="flex p-6 items-start justify-between gap-4">
    <div class="flex items-center gap-3">
      <CustomeCheckBox v-model="item.complete"></CustomeCheckBox>

      <p class="text-gray-300 cursor-pointer" :class="[item.complete ? 'line-through' : '']">
        {{ item.text }}
      </p>
    </div>
    <button @click="deleteItem" class="text-red-500 flex hover:underline items-center">
      <TrashIcon class="h-4 w-4 ml-1"></TrashIcon>Delete
    </button>
  </div>
</template>

<script setup>
import CustomeCheckBox from "./CustomeCheckBox.vue";
import { TrashIcon } from "@heroicons/vue/24/outline";
const props = defineProps(["item"]);
const emits = defineEmits(['deleteItem'])

const deleteItem = () => emits('deleteItem',true);
</script>

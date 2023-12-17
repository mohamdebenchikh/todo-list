<template>
  <label :for="uuid" class="cursor-pointer">
    <div
      class="flex items-center w-5 h-5 rounded-full bg-transparent border border-blue-500 overflow-hidden"
    >
      <input
        :value="modelValue"
        :checked="modelValue"
        @change="$emit('update:modelValue', !modelValue)"
        :id="uuid"
        type="checkbox"
        class="peer sr-only"
      />
      <CheckIcon
        class="h-5 w-5 hidden text-white peer-checked:block peer-checked:bg-blue-500"
      ></CheckIcon>
    </div>
  </label>
</template>
<script setup>
import { CheckIcon } from "@heroicons/vue/24/solid";

function generateRandomString(length) {
  const characters =
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
  let result = "";

  for (let i = 0; i < length; i++) {
    const randomIndex = Math.floor(Math.random() * characters.length);
    result += characters.charAt(randomIndex);
  }

  return result;
}

const uuid = generateRandomString(10);

const props = defineProps(["modelValue"]);
</script>

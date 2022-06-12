<script setup>
import { ref } from 'vue'

const emit = defineEmits(['addItem'])

const newItem = ref('')

const addItem = () => {
  emit('addItem', newItem)
}

</script>

<template>
  <form @submit.prevent="addItem">
    <input 
      v-model="newItem"
      type="text" 
      class="border border-gray-300 rounded-md"
    >
    <button 
      class="bg-green-600 ml-4 py-2 px-4 text-bold text-white rounded-md"
    >
      +
    </button>
  </form>
</template>

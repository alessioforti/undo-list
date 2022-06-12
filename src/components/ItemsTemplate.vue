<script setup>
import { ref } from 'vue'

defineProps({
  items: Array
})

const emit = defineEmits(['done'])

const done = (item) => {
    emit('done', item)
}

</script>

<template>
    <ul class="my-3">
      <li 
        v-for="(item, index) in items" 
        :key="item.id" 
        class="p-3 bg-gray-200 mb-2 rounded-md"
        :class="{ 'line-through text-gray-400 bg-gray-100' : item.done }"
        @click="done(item)"
      >
        {{ item.label }}
      </li>
    </ul>
</template>
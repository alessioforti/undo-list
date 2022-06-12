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
    <ul>
      <li 
        v-for="(item, index) in items" 
        :key="item.id" 
        :class="{ 'line-through text-gray-400' : item.done }"
        @click="done(item)"
      >
        {{ item.label }}
      </li>
    </ul>
</template>
<script setup lang="ts">
import type {inputData}  from '@/App.vue';
type props = {
  data: inputData[] 
}
const emit = defineEmits(['delete-function'])
const deleteFunction = (id : number) => {
  emit('delete-function',id)
}


const props = defineProps<props>()
</script>
<template>
  <div>
    <ul>
      <li v-for="item in props.data" :key="item.id">
        <p>{{item.name}}</p>
        <p>{{item.age}}</p>
        <button @click="deleteFunction(item.id)">DELETE</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>

</style>
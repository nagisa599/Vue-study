<script setup lang="ts">
import { reactive,ref} from 'vue'
import inputFormVue from './components/inputForm.vue';
import userList from './components/userList.vue';
export type inputData = {
  id : number,
  name: string,
  age: number,
}
const data = ref<inputData[]>([])
const postFunction = (inputData:inputData) => {
  const newData = { id : Math.random(), name: inputData.name, age: inputData.age}
  data.value.push(newData);
  inputData.name = '';
  inputData.age = 0;
}
const deleteFunction = (id:number) => {
  const newData = data.value.filter((item) => item.id !== id)
  data.value = newData;
}
</script>

<template>
  <inputFormVue @post-function="postFunction" />
  <userList :data="data" @delete-function="deleteFunction" />
</template>

<style scoped>

</style>

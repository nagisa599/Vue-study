<script setup lang="ts">
import { reactive,defineEmits, computed,ref} from 'vue'
const inputData = reactive({
  name: '',
  age: 0,
})
const checkFlagPost = ref(false)
const emit = defineEmits(['post-function'])
const postFunction = () => {
  emit('post-function',inputData)
}
const error = computed(() => {
  if(inputData.name.length >10){
    checkFlagPost.value = true
    return '10文字以内で入力してください'
  }
})
</script>

<template>
  <div class="inputForm">
    <input type="text" v-model="inputData.name"/>
    <label>{{ error }}</label>
    <input type="number" v-model="inputData.age"/>
    <button @click="postFunction"  v-bind:disabled="checkFlagPost">POST</button>
  </div>

</template>

<style scoped>
.inputForm {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: blue;
  width: 300px;
}
.inputForm input {
  margin: 10px;
}
</style>

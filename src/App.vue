<template>
  <button @click="increase">{{ countRef }}</button>
  <button @click="decrease">{{ countRef }}</button>
</template>

<script>
import { ref } from 'vue'
const useCount = () =>{
  let countRef = ref(0);
  const increase = () => {
    countRef.value++
  }
  const decrease = () => {
    countRef.value--
  }
  return {countRef,increase,decrease}
}
 export default {
  setup(){
    // 返回的所有属性都会暴露给实例模板使用
    return {
      ...useCount()
    }
  }
 }
</script>

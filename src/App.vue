<template>
  <button @click="increase">{{ countRef }}</button>
  <button @click="decrease">{{ countRef }}</button>
</template>

<script>
import { ref } from 'vue'

/**
 * 计数器自定义组合式API
 * 可以单独封装起来
 * @returns 返回包含计数器的引用、增加和减少计数的方法的对象
 */
const useCount = () =>{
  let countRef = ref(0); // 命名格式必有Ref结尾
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
    // 只要是在setup中，countRef就是一个对象
    // 实例代理中，countRef就是countRef.value
    return {
      // 返回的所有属性都会暴露给实例模板使用
      ...useCount()
    }
  }
 }
</script>

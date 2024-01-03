<template>
  <div class="container">
    <music-com :books="books" @del="handleDel"></music-com>
  </div>
</template>

<script setup>
import MusicCom from '@/components/MusicCom.vue';
import axios from 'axios'
import { ref, onMounted, BaseTransitionPropsValidators } from 'vue';
const books = ref([])
onMounted(async () => {
  const res = await axios.get('http://39.103.151.139:8000/book')
  // console.log(res.data)
  books.value = res.data
})
const handleDel = (id) => {
  // console.log(id)
  if (window.confirm('请确认要删除这个吗?')) { books.value.splice(id, 1) }

}
</script>

<style  scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  text-align: center;

}
</style>
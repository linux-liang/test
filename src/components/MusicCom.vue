<template>
    <div class="item" v-for="(book, index) of  books " :key="index" @click="handleSend(index)">
        <img :src="book.coverImage" alt="">
        <p>{{ book.title.slice(0, 6) }}</p>
    </div>
</template>

<script setup>
defineProps({
    books: Object
})
const emits = defineEmits(['del'])
const handleSend = (index) => {
    emits('del', index)
}
</script>

<style scoped>
.item {
    width: 200px;
    height: 200px;
    border: 1px solid black;
    margin: 10px;
    padding: 10px;
    /* overflow: hidden; */
}

.item img {
    width: 150px;
    height: 150px;
}
</style>
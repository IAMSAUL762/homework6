<script setup>
import { onMounted, ref } from 'vue'
import BaseTitle from '@/components/BaseTitle.vue';
import useAPI from '@/Composables/useAPI'
import MainScore from '@/components/MainScore.vue';

const { categories, getCategories } = useAPI()

onMounted(async () => {
  await getCategories()
})    


</script>

<template>
  <BaseTitle>TRIVIA APPLICATION - <MainScore></MainScore> </BaseTitle>
  <div class="grid flex-grow grid-cols-4 gap-12 m-20">
  <router-link v-for="category in categories" 
    :key="category.id"
    :to="`/Question/categories/${category.id}`"
    class="bg-white text-center flex h-32 items-center justify-center rounded-lg boarder-4 border-slate-500 py-4 font-bold uppercase hover:cursor pointer hover:boarder-red-500 hover-bg-red-400 hover:text-white transition-colors duration-300"
  >
    {{ category.name }}
  </router-link>  
    </div> 
</template>

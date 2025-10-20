<script setup>
import { onMounted, ref } from 'vue'
import { useAPI } from '@/Composables/useAPI';
import { useRoute } from 'vue-router'; 
import BaseTitle from '@/components/BaseTitle.vue';
const route = useAPI()
const Questions = ref(null)
const route = useRoute()

onMounted(async () => {
  Questions.value = await api.getQuestions(route.params.id)
})    

</script> 



<template>
  
<div v-if="question" class="">
  <BaseTitle>{{  Questions.category }}</BaseTitle>
  {{ Question.question }}
</div>
<div v-else classe="">
  Loading...
</div>

</template>

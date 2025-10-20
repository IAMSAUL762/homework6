<script setup>
import { onMounted, ref } from 'vue'
import { useAPI } from '@/Composables/useAPI';
import { useRoute } from 'vue-router'; 

const route = useAPI()
const Questions = ref(null)
const route = useRoute()

onMounted(async () => {
  Questions.value = await api.getQuestions(route.params.id)
})    

</script> 

<template>
{{ question }}
</template>

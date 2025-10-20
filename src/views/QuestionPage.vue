<script setup>
import { onMounted, ref } from 'vue';
import { useAPI } from '@/Composables/useAPI';
import { useRoute } from 'vue-router';
import BaseTitle from '@/components/BaseTitle.vue';
const route = useAPI()
const Questions = ref(null)
const route = useRoute()
const answer = ref({ }) 
onMounted(async () => {
  Questions.value = await api.getQuestions(route.params.id)

  answer.value.push({
    id: answers.value.length,
    correct: true,
    answer: question.value.correct_answer
  })

  question.value.incorrect_answers.map((wrong_answer) => {
    answer.value.push({
      id: answers.value.length,
      correct: false,
      answer: wrong_answer
    })

  })

answers.value = shuffle(answers.value)
//console.log(question.value)
})

const shuffle = (array) => {
  for (let i = array.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    //swap
    [array[i], array[j]] = [array[j], array[i]];
  }

  return array;
}



</script> 



<template>

<div v-if="question" class="">
  <BaseTitle>{{  Questions.category }}</BaseTitle>
  {{ Question.question }}
  <div v-for="answer in answers" v-html="answer.answer" :key="answer.id" class=""></div>
  </div>
<div v-else class="">
  Loading...
</div>

</template>

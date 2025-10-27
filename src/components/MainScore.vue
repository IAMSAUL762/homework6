<script setup>
import useScore from '@/Composables/useScore';
const { score } = useScore()
</script>

<template>
    <span class="">Main Score: {{ score }}</span>
</template>


  
<script setup>
import { ref } from 'vue'
import HelloWorld from './HelloWorld.vue'

// ВІДРЕДАГУЙТЕ СВОЇ ДАНІ
const student = {
  specialty: 'Кібербезпека та захист інформації',
  course: 4,
  group: '2БС-23б',
  fullName: 'Савкун Валентин Олександрович',
}

const likes = ref(0)
const onLike = () => likes.value++
</script>

<template>
  <HelloWorld msg="Vue + Vite + Docker" :student="student" :likes="likes" @like="onLike" />
</template>

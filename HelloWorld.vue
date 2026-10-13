<script setup>
import { computed } from 'vue'

// Властивості (props): дані передаються вниз від батька
const props = defineProps({
  msg: { type: String, required: true },
  student: { type: Object, required: true },
  likes: { type: Number, default: 0 },
})

// Власна подія (emit): дочірній компонент повідомляє батька
const emit = defineEmits(['like'])

// Масив для директиви v-for
const rows = computed(() => [
  { label: 'Спеціальність', value: props.student.specialty },
  { label: 'Курс', value: props.student.course },
  { label: 'Група', value: props.student.group },
  { label: 'ПІБ', value: props.student.fullName },
])
</script>

<template>
  <section class="card">
    <h1>{{ msg }}</h1>

    <ul class="info">
      <li v-for="row in rows" :key="row.label">
        <span class="label">{{ row.label }}:</span>
        <strong>{{ row.value }}</strong>
      </li>
    </ul>

    <button class="btn" @click="emit('like')">👍 Лайк</button>
    <p v-if="likes > 0" class="likes">Лайків: {{ likes }}</p>
    <p v-else class="likes muted">Лайків ще немає</p>
  </section>
</template>

<style scoped>
.card {
  background: #fff;
  border-radius: 16px;
  padding: 24px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
}
h1 {
  margin-top: 0;
  font-size: 1.4rem;
}
.info {
  list-style: none;
  padding: 0;
  margin: 16px 0;
  display: grid;
  gap: 8px;
}
.label {
  color: #6b7280;
  margin-right: 6px;
}
.btn {
  padding: 10px 18px;
  border: 0;
  border-radius: 10px;
  background: #42b883;
  color: #fff;
  font-weight: 600;
  cursor: pointer;
}
.btn:hover {
  background: #35a273;
}
.likes {
  margin-top: 12px;
}
.muted {
  color: #9ca3af;
}
</style>

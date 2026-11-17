<script setup>
import { ref, computed } from 'vue'
const count = ref  (3)
const total = computed(() => count.value * 12)
</script>

<template>
  <div class="mt-8 rounded-xl bg-slate-100 p-6 text-slate-900 max-w-md">
    <label>Quantity <input v-model.number="count" type="range" min="1" max="10" class="ml-4" /></label>
    <p class="mt-4">{{ count }} × 12 = <strong>{{ total }}</strong></p>
  </div>
</template>

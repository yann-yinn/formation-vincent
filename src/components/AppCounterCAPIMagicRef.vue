<script setup lang="ts">
import { defineProps, watch, onMounted, type PropType } from "vue";

defineProps({
  initialCount: {
    type: Number as PropType<number>,
    required: true,
  },
});

let counter = $ref(0);
let counterDouble = $ref(0);

const increment = () => {
  counter += 1;
};

watch($$(counter), (value) => {
  counterDouble = value * 2;
});

/**
 * 1) Tracking de dépendance automatiquement
 * 2) créer une variable reactive et la mettre à jour quand une dépendance change
 */
const counterTriple = $computed(() => {
  return counter * 3;
});

onMounted(() => {
  console.log("coucou");
});
</script>

<template>
  <div>
    <h1>Counter</h1>
    <h2>{{ counter }}</h2>
    <h3>Double: {{ counterDouble }}</h3>
    <h3>Triple: {{ counterTriple }}</h3>
    <button @click="increment">add</button>
  </div>
</template>

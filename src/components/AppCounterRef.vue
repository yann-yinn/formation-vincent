<script setup lang="ts">
import {
  defineProps,
  ref,
  watch,
  computed,
  onMounted,
  type PropType,
} from "vue";

/*
interface Props {
  color: "blue" | "red";
}
defineProps<Props>()
*/

defineProps({
  initialCount: {
    type: Number as PropType<number>,
    required: true,
  },
});

let counter = ref(0);
const counterDouble = ref(0);

console.log("counter", counter);

const increment = () => {
  counter.value += 1;
};

watch(counter, (value) => {
  counterDouble.value = value * 2;
});

/**
 * 1) Tracking de dépendance automatiquement
 * 2) créer une variable reactive et la mettre à jour quand une dépendance change
 */
const counterTriple = computed(() => {
  return counter.value * 3;
});

onMounted(() => {
  alert("coucou");
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

<script setup lang="ts">
import {
  defineProps,
  ref,
  watch,
  computed,
  onMounted,
  reactive,
  type PropType,
} from "vue";

/*
interface Props {
  color: "blue" | "red";
}
defineProps<Props>()
*/

const props = defineProps({
  initialCount: {
    type: Number as PropType<number>,
    required: true,
  },
});

const state = reactive({
  counter: props.initialCount,
  counterDouble: 0,
});

// ces deux notation créer la même variable réactive ! (en gros)
/*
let counter = ref(0);
let counter = reactive({ value: 0 });
*/

const increment = () => {
  state.counter += 1;
};

watch(
  () => state.counter,
  (value) => {
    state.counterDouble = value * 2;
  }
);

/**
 * 1) Tracking de dépendance automatiquement
 * 2) créer une variable reactive et la mettre à jour quand une dépendance change
 */
const counterTriple = computed(() => {
  return state.counter * 3;
});

onMounted(() => {
  console.log("onmounted");
});
</script>

<template>
  <div>
    <h1>Counter</h1>
    <h2>{{ state.counter }}</h2>
    <h3>Double: {{ state.counterDouble }}</h3>
    <h3>Triple: {{ counterTriple }}</h3>
    <button @click="increment">add</button>
  </div>
</template>

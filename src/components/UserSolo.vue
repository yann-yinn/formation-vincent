<template>
  <div>
    <p>{{ user.name }}</p>
    <p>{{ user.email }}</p>
  </div>
</template>

<script setup lang="ts">
import type { PropType } from "vue";
import type { User } from "@/types/User";

const props = defineProps({
  user: {
    type: Object as PropType<User>,
    required: true,
  },
});
</script>

<style></style>

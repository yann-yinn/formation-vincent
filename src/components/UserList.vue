<template>
  <div>
    <UserSolo v-for="user in users" :key="user.id" :user="user" />
  </div>
</template>

<script setup lang="ts">
import type { User } from "@/types/User";
import type { PropType } from "vue";
import UserSolo from "@/components/UserSolo.vue";

// interface Props {
//   users: User[]
// }

// const props =  defineProps<Props>()

const props = defineProps({
  users: {
    type: Array as PropType<User[]>,
    required: true,
  },
});
</script>

<style></style>

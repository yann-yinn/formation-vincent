<template>
  <UserList v-if="users !== null" :users="users" />
  <p v-if="state.loading">Loading</p>
  <p v-if="state.error">{{ state.error }}</p>
</template>

<script setup lang="ts">
import axios from "axios";
import UserList from "@/components/UserList.vue";
import { reactive, ref } from "vue";

interface User {
  id: number;
  name: string;
  email: string;
}

interface State {
  loading: boolean;
  error: string | null;
}

const users = ref<User[] | null>(null);
const state = reactive<State>({
  loading: false,
  error: null,
});

const loadData = async () => {
  state.loading = true;
  try {
    const response = await axios.get<User[]>(
      "https://jsonplaceholder.typicode.com/users"
    );
    users.value = response.data;
  } catch (error) {
    state.error = error as string;
    state.loading = false;
  }
  state.loading = false;
};

loadData();
</script>

<style></style>

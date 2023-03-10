<script setup lang="ts">
import axios from 'axios';
import { useQueryClient, useQuery, useMutation } from '@tanstack/vue-query';
// Access QueryClient instance
const queryClient = useQueryClient();

const getData = async () => {
  const { data } = await axios.get('https://swapi.dev/api/people/9');
  return data;
};

// Query
const { isLoading, isError, data, error } = useQuery({
  queryKey: ['todos_02'],
  queryFn: getData
});

console.log('data', data);
</script>

<template>
  <div>
    <div>
      <router-link to="/">Go to Home</router-link>
    </div>
    <p>Page02</p>
    <p v-if="!isLoading">name: {{ data.name }}</p>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

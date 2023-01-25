<script setup lang="ts">
import { useCounterStore } from "@/stores/counter";
const counterStore = useCounterStore();
</script>
<template>
  <div>Second Component</div>
  <div>{{ counterStore.doubleCount }}</div>
</template>

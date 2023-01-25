<script setup lang="ts">
import { useCounterStore } from "@/stores/counter";
const counterStore = useCounterStore();
</script>
<template>
  <div>First Component</div>
  <div>{{ counterStore.count }}</div>
</template>

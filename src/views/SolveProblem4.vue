<script setup lang="ts">
import FirstComponent from "@/components/FirstComponent.vue";
import SecondComponent from "@/components/SecondComponent.vue";
import { useCounterStore } from "../stores/counter";
const counterStore = useCounterStore();
</script>
<template>
  <v-container>
    <v-row>
      <v-col cols="6">
        <FirstComponent></FirstComponent>
      </v-col>
      <v-col cols="6">
        <SecondComponent></SecondComponent>
      </v-col>
      <v-col cols="6"
        ><v-btn @click="counterStore.increment()">Increment</v-btn></v-col
      >
      <v-col cols="6"
        ><v-btn @click="counterStore.decrement()">Decrement</v-btn></v-col
      >
    </v-row>
  </v-container>
</template>

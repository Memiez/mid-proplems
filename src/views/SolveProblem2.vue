<script lang="ts" setup>
import { computed, ref } from "vue";
const numberStr = ref("0");
const number = computed(() => {
  return parseInt(numberStr.value);
});
</script>

<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-text-field
          v-model="numberStr"
          :rules="[(v) => !!v || 'Number is not empty!']"
          label="Input Number"
          required
        >
        </v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <v-container>
          <v-row>
            <v-col cols="1" v-for="num of number" :key="num">{{ num }}</v-col>
          </v-row>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
</template>

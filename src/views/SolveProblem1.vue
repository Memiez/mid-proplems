<script lang="ts" setup>
import { computed, ref } from "vue";
const feelings = ref(["angry", "cute", "excited", "pain", "shocked", "smile"]);
const currentFelling = ref("smile");
const showCurrentFeeling = computed(() => {
  return (
    currentFelling.value.toUpperCase().charAt(0) + 
    currentFelling.value.substring(1)
  );
});
</script>
<template>
  <v-container>
    <v-row>
      <v-col
        ><v-img style="height: 50vh" :src="`${currentFelling}.png`"></v-img
      ></v-col>
      <v-col>
        <v-container style="background-color: gray">
          <v-row>
            <v-col cols="12">
              <div width="100%" class="text-h3 text-center">
                {{ showCurrentFeeling }}
              </div>
            </v-col>
            <v-col
              v-for="(feeling, index) of feelings"
              cols="12"
              width="100%"
              :key="index"
            >
              <v-btn
                width="100%"
                @click="currentFelling = feeling"
                :class="{ btnColor: currentFelling === feeling }"
              > <!--ทำให้ปุ่มเปลี่ยนสีเมื่อ click -->
                {{ feeling }}</v-btn
              >
            </v-col>
          </v-row>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
.btnColor {
  background-color: slateblue;
}
</style>

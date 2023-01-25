<script lang="ts" setup>
import { computed, ref } from "vue";
interface Product {
  id: number;
  name: string;
  price: number;
}
const products = ref(
  Array.from(Array(100).keys()).map((item) => {
    return {
      id: item,
      name: "Product " + (item + 1),
      price: (Math.floor(Math.random() * 100) + 1) * 10,
    };
  })
);
const orderItem = ref<Product[]>([]);
const addProduct = (product: Product) => {
  orderItem.value.push(product);
};
const total = computed(() => {
  let sum = 0;
  for (const p of orderItem.value) {
    sum = sum = p.price;
  }
  return sum;
});
</script>
<template>
  <v-container>
    <v-row>
      <v-col cols="6" style="overflow-y: auto; height: 70vh">
        <v-container>
          <v-row>
            <v-col cols="4" v-for="product of products" :key="product.id">
              <v-card class="pa-5 text-center">
                <v-card-title>{{ product.name }}</v-card-title>
                <v-card-text>{{ product.price }}</v-card-text>
                <v-card-action>
                  <v-btn color="pink" @click="addProduct(product)"
                    >Add More</v-btn
                  ></v-card-action
                >
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-col>
      <v-col cols="6">
        <v-container>
          <v-row style="overflow-y: auto; height: 70vh">
            <v-col cols="12">
              <v-table>
                <thead>
                  <tr>
                    <th>#ID</th>
                    <th>Name</th>
                    <th>Price</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-if="orderItem.length === 0">
                    <td colspan="3" class="text-center">No Data</td>
                  </tr>
                  <tr v-for="(product, index) of orderItem" :key="index">
                    <td>{{ product.id }}</td>
                    <td>{{ product.name }}</td>
                    <td>{{ product.price }}</td>
                  </tr>
                </tbody>
              </v-table>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="12" class="text-h5"> Sum {{ total }}</v-col>
          </v-row>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
</template>

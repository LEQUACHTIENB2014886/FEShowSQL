<template>
  <div id="app">
    <loading v-if="isLoading" text="Loading..." />
    <div v-else>
      <Table />
      <ExcelReader />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import Loading from "./components/Loading.vue";
import Table from "./components/Table.vue";
import ExcelReader from "./components/ExcelReader.vue";

const isLoading = ref(true); //

// Khi component được mounted, sẽ tắt loading sau 
onMounted(() => {
  setTimeout(() => {
    isLoading.value = false;
  }, 1500);
});
</script>

<style>
#app {
  text-align: center;
  margin-top: 50px;
}
</style>
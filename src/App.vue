<script setup>
import VExpansion from "./components/VExpansion.vue";
import { ref } from "vue";
const data = ref([
  {
    id: 1,
    data: "Phú Trạch",
    grade: 1,
    pid: null,
  },
  {
    id: 2,
    data: "Thắng lợi",
    grade: 1,
    pid: null,
  },
  {
    id: 3,
    data: "Đội 9",
    grade: 2,
    pid: 1,
  },
  {
    id: 4,
    data: "Đội 8",
    grade: 2,
    pid: 1,
  },
  {
    id: 5,
    data: "Xóm abc",
    grade: 3,
    pid: 3,
  },
  {
    id: 6,
    data: "Đội 100",
    grade: 2,
    pid: 2,
  },
  {
    id: 7,
    data: "Xóm xyz",
    grade: 3,
    pid: 3,
  },
  {
    id: 8,
    data: "hihi",
    grade: 4,
    pid: 7,
  },
]);
</script>

<template>
  <VExpansion :data="data" width="200">
  </VExpansion>
</template>

<style scoped>
</style>

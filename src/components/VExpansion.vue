<template>
  <v-expansion-panels variant="accordion" multiple>
    <v-expansion-panel
      v-for="item in dataConverted"
      :key="item.id"
      :title="item.data"
      :style="{'width': props.width +'px'}"
    >
      <v-expansion-panel-text>
        <VExpansion
          v-if="item.child"
          :data="item.child"
          :isBuildTree="false"
        ></VExpansion>
      </v-expansion-panel-text>
    </v-expansion-panel>
  </v-expansion-panels>
</template>

<script setup>
import { ref, defineProps, onMounted } from "vue";

const props = defineProps({
  data: {
    type: Array,
    default: [],
  },
  isBuildTree: {
    type: Boolean,
    default: true,
  },
  width:{
    type: String,
    default: "200",
  }
});
const dataConverted = ref([]);

onMounted(() => {
  if (props.isBuildTree) dataConverted.value = buildTree(props.data, null);
  else dataConverted.value = props.data;
});

// chuyển đổi mảng theo cấu trúc cây
function buildTree(list, parentId = null) {
  const result = [];
  list
    .filter((item) => item.pid === parentId)
    .forEach((item) => {
      const children = buildTree(list, item.id);
      if (children.length > 0) {
        item.child = children;
      } else {
        item.child = [];
      }
      result.push(item);
    });
  return result;
}
</script>

<style lang="scss" scoped>
</style>
<template>
  <el-radio-group
    @click="isMenu"
    v-model="isCollapse"
    style="margin-bottom: 20px"
  >
    <el-radio-button :label="false">expand</el-radio-button>
    <el-radio-button :label="true">collapse</el-radio-button>
  </el-radio-group>
</template>

<script lang="ts" setup>
import { defineEmits, ref } from "vue";
const isCollapse = ref(true);
const clickCount = ref<number>(0);

const emits = defineEmits<{
  (event: "showMenu", data: boolean): void;
}>();

const isMenu = () => {
  clickCount.value++;
  if (clickCount.value === 1) emits("showMenu", !isCollapse.value);
  if (clickCount.value > 1) clickCount.value = 0;
};
</script>

<style></style>

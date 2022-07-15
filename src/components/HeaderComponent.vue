<template>
  <div class="header bg-dark">
    <div>
      <div @click="isMenu" class="menu-icon">
        <i class="fa-solid fa-bars"></i>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { defineEmits, ref } from "vue";
const isCollapse = ref(true);
const clickCount = ref<number>(0);

const emits = defineEmits<{
  (event: "showMenu", data: boolean): void;
}>();

const isMenu = () => {
  isCollapse.value = !isCollapse.value;
  emits("showMenu", !isCollapse.value);
};
</script>

<style lang="scss" scoped>
.header {
  width: 100vw;
  height: 100%;
  display: flex;
  flex-direction: row nowrap;
}
.menu-icon {
  color: #fff;
  height: 100%;
  width: 30px;
  margin-top: 50%;
  margin-left: 50%;
  cursor: pointer;
}
</style>

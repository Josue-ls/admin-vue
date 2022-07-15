<template>
  <el-container>
    <el-header>
      <header-component @show-menu="isMenu" />
    </el-header>
    <el-container>
      <el-aside>
        <aside-component :isCollapse="isCollapse" />
      </el-aside>
      <el-container>
        <el-main>
          <main-component />
        </el-main>
        <el-footer>
          <footer-component />
        </el-footer>
      </el-container>
    </el-container>
  </el-container>
</template>

<script lang="ts" setup>
import { onMounted, ref } from "vue";
import HeaderComponent from "./HeaderComponent.vue";
import MainComponent from "./MainComponent.vue";
import AsideComponent from "./AsideComponent.vue";
import FooterComponent from "./FooterComponent.vue";

const isCollapse = ref<boolean>(true);
const isMenu = (showMenu: boolean) => {
  isCollapse.value = showMenu;
  const menu = document.querySelectorAll(".el-aside");
  if (showMenu) {
    menu?.forEach((element) => {
      element.classList.remove("el-aside--open");
      element.classList.add("el-aside--collapse");
    });
  } else {
    menu?.forEach((element) => {
      element.classList.remove("el-aside--collapse");
      element.classList.add("el-aside--open");
    });
  }
};

onMounted(() => {
  const menu = document.querySelectorAll(".el-aside");
  menu?.forEach((element) => {
    element.classList.remove("el-aside--open");
    element.classList.add("el-aside--collapse");
  });
});
</script>

<style lang="scss" scoped>
$height: 91vh;
.el-header {
  --el-header-padding: 0px !important;
  --el-header-height: 9vh !important;
}
.el-aside--open {
  overflow: auto;
  box-sizing: border-box;
  flex-shrink: 0;
  width: var(--el-aside-width, 300px);
  height: $height;
  transition: all 0.5s;
}

.el-aside--collapse {
  overflow: auto;
  box-sizing: border-box;
  flex-shrink: 0;
  width: var(--el-aside-width, 70px);
  height: $height;
  transition: all 0.5s;
}

.el-menu--collapsed {
  width: 70px;
  height: 100% !important;
}
</style>

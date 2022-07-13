<template>
  <div class="common-layout">
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
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import HeaderComponent from "./HeaderComponent.vue";
import MainComponent from "./MainComponent.vue";
import AsideComponent from "./AsideComponent.vue";
import FooterComponent from "./FooterComponent.vue";

const isCollapse = ref<boolean>(true);
const isMenu = (showMenu: boolean) => {
  isCollapse.value = showMenu;
};
</script>

<style></style>

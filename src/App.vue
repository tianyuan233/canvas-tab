<script setup lang="ts">
import { ref, onMounted } from "vue";
import NavCanvas from "./util/NavCanvas";

const nc = ref();

const tabList = [
  "大屏管理",
  "组件库",
  "地图管理",
  "分类管理",
  "数据源管理",
  "数据集管理",
  "综合功能",
];

const onTabClick = (index: number) => {
  nc.value?.toggle(index);
};

onMounted(() => {
  nc.value = new NavCanvas("nav-canvas", ".nav-main .nav-span", 0);
});
</script>

<template>
  <div class="nav-wrapper">
    <div data-v-e16b8822="" class="nav-main">
      <canvas
        data-v-e16b8822=""
        id="nav-canvas"
        style="
          position: absolute;
          z-index: -1;
          left: 0px;
          width: 1920px;
          height: 70px;
        "
        width="3840"
        height="140"
      ></canvas>
      <span
        v-for="(tab, index) in tabList"
        class="nav-span"
        @click="onTabClick(index)"
      >
        <a data-v-e16b8822="" class="nav-link">
          {{ tab }}
        </a>
      </span>
    </div>
  </div>
</template>

<style scoped>
.nav-wrapper {
  background-color: #202023;
}

.nav-main {
  width: 100%;
  padding-bottom: 10px;
  position: relative;
  z-index: 999;
  display: flex;
  width: 100%;
  user-select: none;
  height: 60px;
}

.nav-main .nav-span .nav-link {
  -webkit-transition: color 0.2s;
  transition: color 0.2s;
  text-decoration: none !important;
  display: block;
  color: #b9c2cc;
  width: auto;
  min-width: 140px;
  line-height: 60px;
  font-size: 14px;
  text-align: left;
  cursor: pointer;
  padding: 0 40px;
  text-align: center;
}
</style>

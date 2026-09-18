<script setup lang="ts">
import { ref } from "vue";

const isOpen = ref(false);
const closeMenu = () => {
  isOpen.value = false;
};
</script>

<template>
  <header class="shell">
    <div class="topbar">
      <a class="brand" href="#" aria-label="Savoria 首页" @click="closeMenu"><span class="brand-mark">S</span>SAVORIA</a>
      <button class="menu-toggle" type="button" aria-label="打开菜单" :aria-expanded="isOpen" @click="isOpen = !isOpen">&#9776;</button>
      <nav class="nav" :class="{ open: isOpen }" aria-label="主导航">
        <a href="#menu" @click="closeMenu">今日菜单</a>
        <a href="#story" @click="closeMenu">我们的故事</a>
        <a href="#visit" @click="closeMenu">来店方式</a>
        <a class="nav-cta" href="#reserve" @click="closeMenu">预订座位</a>
      </nav>
    </div>
  </header>
</template>

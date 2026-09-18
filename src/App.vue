<script setup lang="ts">
import HeaderNav from "./components/HeaderNav.vue";
import HeroSection from "./components/HeroSection.vue";
import MenuSection from "./components/MenuSection.vue";
import ReservationSection from "./components/ReservationSection.vue";
import SiteFooter from "./components/SiteFooter.vue";
import StorySection from "./components/StorySection.vue";
</script>

<template>
  <HeaderNav />
  <main>
    <HeroSection />
    <section id="visit" class="shell intro-strip">
      <h2 class="display">好食物不需要<br /><em>复杂的解释。</em></h2>
      <p>从农场到餐桌，我们只走最短的路。每天从附近农场、渔港和面包房挑选食材，随着季节改变菜单，也让每次到访都有新发现。</p>
    </section>
    <MenuSection />
    <StorySection />
    <ReservationSection />
  </main>
  <SiteFooter />
</template>

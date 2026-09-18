<script setup lang="ts">
import { computed, ref } from "vue";

type Category = "all" | "small" | "main" | "sweet";
interface Dish {
  name: string;
  description: string;
  price: string;
  category: Exclude<Category, "all">;
  image: string;
  alt: string;
}
interface Filter {
  label: string;
  value: Category;
  icon: string;
}

const activeFilter = ref<Category>("all");
const filters: Filter[] = [
  { label: "全部", value: "all", icon: "✦" },
  { label: "前菜", value: "small", icon: "◌" },
  { label: "主菜", value: "main", icon: "⌁" },
  { label: "甜点", value: "sweet", icon: "◒" },
];
const dishes: Dish[] = [
  { name: "番茄 · 海盐 · 云朵芝士", description: "熟成番茄 / 罗勒油 / 烤酸面包", price: "¥20", category: "small", image: "https://images.unsplash.com/photo-1505253716362-afaea1d3d1af?auto=format&fit=crop&w=900&q=85", alt: "番茄和奶酪前菜" },
  { name: "炭烤章鱼与白豆", description: "烟熏红椒 / 青柠 / 香草白豆泥", price: "¥168", category: "main", image: "https://images.unsplash.com/photo-1515003197210-e0cd71810b5f?auto=format&fit=crop&w=900&q=85", alt: "炭烤海鲜主菜" },
  { name: "橄榄油柑橘蛋糕", description: "血橙 / 酸奶奶油 / 开心果", price: "¥58", category: "sweet", image: "https://images.unsplash.com/photo-1551024506-0bccd828d307?auto=format&fit=crop&w=900&q=85", alt: "精致的甜点" },
];
const visibleDishes = computed(() => activeFilter.value === "all" ? dishes : dishes.filter((dish) => dish.category === activeFilter.value));
const countFor = (category: Category) => category === "all" ? dishes.length : dishes.filter((dish) => dish.category === category).length;
</script>

<template>
  <section id="menu" class="shell menu-section">
    <div class="section-head">
      <div><div class="eyebrow">The short list</div><h2 class="display">今日菜单</h2></div>
      <div class="menu-filters" role="group" aria-label="菜单分类">
        <button v-for="filter in filters" :key="filter.value" class="filter" :class="{ active: activeFilter === filter.value }" type="button" @click="activeFilter = filter.value">
          <span>{{ filter.icon }}</span>{{ filter.label }}<span class="filter-count">{{ countFor(filter.value) }}</span>
        </button>
      </div>
    </div>
    <div class="dish-grid">
      <article v-for="(dish, index) in visibleDishes" :key="dish.name" class="dish-card" :class="{ 'dish-card-offset': index === 1 }">
        <div class="dish-photo"><img :src="dish.image" :alt="dish.alt" /></div>
        <div class="dish-info"><div><h3 class="dish-name">{{ dish.name }}</h3><p class="dish-desc">{{ dish.description }}</p></div><div class="dish-price">{{ dish.price }}</div></div>
      </article>
    </div>
  </section>
</template>

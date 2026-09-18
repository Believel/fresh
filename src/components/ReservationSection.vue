<script setup lang="ts">
import { ref } from "vue";

const submitted = ref(false);
const handleSubmit = () => {
  submitted.value = true;
};
</script>

<template>
  <section id="reserve" class="shell reservation">
    <div class="reservation-copy">
      <div class="eyebrow">Come as you are</div>
      <h2 class="display">留一盏灯，等你来。</h2>
      <p>晚餐时段座位有限，建议提前预订。午餐欢迎直接到店，我们会尽力为你安排一张舒服的桌子。</p>
      <div class="reservation-details">
        <div><div class="detail-label">营业时间</div><div class="detail-value">周二至周日<br />11:30 — 22:30</div></div>
        <div><div class="detail-label">地址</div><div class="detail-value">上海市安福路 118 号<br />Savoria 一层</div></div>
      </div>
    </div>
    <form class="booking-form" @submit.prevent="handleSubmit">
      <h3>预订一张桌子</h3>
      <div class="form-row">
        <div class="field"><label for="date">日期</label><input id="date" type="date" required /></div>
        <div class="field"><label for="time">时间</label><select id="time"><option>18:30</option><option>19:00</option><option>19:30</option><option>20:00</option><option>20:30</option></select></div>
      </div>
      <div class="form-row">
        <div class="field"><label for="guests">人数</label><select id="guests"><option>2 位客人</option><option>3 位客人</option><option>4 位客人</option><option>5 位客人</option><option>6 位客人</option></select></div>
        <div class="field"><label for="name">称呼</label><input id="name" type="text" placeholder="你的名字" required /></div>
      </div>
      <div class="form-submit"><button class="button" type="submit">{{ submitted ? "已提交" : "查找座位" }}</button><span v-if="submitted" class="form-message">已收到你的请求，我们会尽快与你确认。</span></div>
    </form>
  </section>
</template>

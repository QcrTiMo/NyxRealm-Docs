---
layout: page
gitChangelog: false
pageProperties: false
---

<script setup>
import { ref, computed } from 'vue';
import Card from './.vitepress/theme/components/Card.vue';

const creditsData = ref([
  {
    name: 'NapCatQQ',
    image: '/assets/images/thank/napcat.png',
    description: [
      '感谢他们的主题样式',
      '感谢NapCatQQ对QQoneBot的支持',
    ],
    link: 'https://napneko.github.io/#',
    linkText: '访问官网'
  },
]);

const currentIndex = ref(0);
const totalSlides = computed(() => creditsData.value.length);

function setIndex(index) {
  currentIndex.value = index;
}

function getCardStyle(index) {
  const offset = index - currentIndex.value;
  const isVisible = Math.abs(offset) < 2;

  if (!isVisible) {
    return { transform: `translateX(${offset * 100}%) scale(0.8)`, opacity: 0, zIndex: 0, cursor: 'pointer' };
  }

  const translateX = offset * 70;
  const scale = offset === 0 ? 1 : 0.85;
  const opacity = offset === 0 ? 1 : 0.5;
  const zIndex = totalSlides.value - Math.abs(offset);
  const cursor = offset === 0 ? 'default' : 'pointer';

  return {
    transform: `translateX(${translateX}%) scale(${scale})`,
    opacity: opacity,
    zIndex: zIndex,
    cursor: cursor,
  };
}
</script>

<style>
.credits-page-container {
  overflow-x: hidden;
  box-sizing: border-box;
  padding-top: 10vh;
  padding-bottom: 120px;
}
.credits-carousel-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
}
.carousel-track {
  position: relative;
  width: 800px;
  height: 450px;
  max-width: 90vw;
  perspective: 1000px;
}
.carousel-item {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transition: transform 0.5s ease, opacity 0.5s ease;
}
.credit-card {
  width: 100%;
  height: 100%;
  display: flex;
  background-color: var(--vp-c-bg-soft);
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}
.card-image {
  flex: 0 0 450px;
  height: 100%;
  padding: 16px;
  box-sizing: border-box;
}
.card-content {
  flex: 1;
  padding: 32px 40px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.card-content h3 {
  margin: 0 0 20px 0;
  padding: 0;
  font-size: 2.5em;
  font-weight: 600;
  border: none;
  color: var(--vp-c-brand-1);
}
.card-content ul {
  list-style-type: '✓ ';
  margin: 0 0 28px 0;
  padding-left: 20px;
  color: var(--vp-c-text-2);
}
.card-content ul li {
  margin-bottom: 10px;
  line-height: 1.6;
  font-size: 1em;
}
.card-content a {
  display: inline-block;
  align-self: flex-start;
  background-color: var(--vp-c-brand-1);
  color: var(--vp-c-bg-soft) !important;
  padding: 10px 20px;
  border-radius: 8px;
  text-decoration: none !important;
  font-weight: 500;
  transition: background-color 0.2s;
  font-size: 1em;
}
.card-content a:hover {
  background-color: var(--vp-c-brand-2);
}
.credits-page-title {
  text-align: center;
  font-size: 3em;
  margin-bottom: 24px;
}
</style>

<div class="credits-page-container">
  <h1 class="credits-page-title">特别鸣谢</h1>
  <div class="credits-carousel-wrapper">
    <div class="carousel-track">
      <div
        v-for="(credit, index) in creditsData"
        :key="credit.name"
        class="carousel-item"
        :style="getCardStyle(index)"
        @click="setIndex(index)"
      >
        <div class="credit-card">
          <div class="card-image">
            <Card>
              <img :src="credit.image" :alt="credit.name" />
            </Card>
          </div>
          <div class="card-content">
            <h3>{{ credit.name }}</h3>
            <ul>
              <li v-for="item in credit.description" :key="item">{{ item }}</li>
            </ul>
            <a :href="credit.link" target="_blank" rel="noopener noreferrer">
              {{ credit.linkText }} &rarr;
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
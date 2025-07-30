<script setup>
import '../assets/detail.css'
import { useRoute, useRouter } from 'vue-router'
import portfolioData from '../js/portfolioData.js'
import { computed } from 'vue'

const route = useRoute()
const router = useRouter()
const id = parseInt(route.params.id)

// 해당 id에 맞는 포트폴리오 데이터 찾기
const selected = computed(() =>
  portfolioData.find((item) => item.id === id)
)

function goBack() {
  if (window.history.length > 1) {
    router.back()
  } else {
    router.push('/')  // 대체 이동
  }
}
</script>

<template>
  <section id="detail" v-if="selected">
    <div class="back" @click="goBack">← Back</div>
    <div class="wrap">
      <h2>{{ selected.title }}</h2>
      <div class="flex">
        <div class="d-left">
          <img :src="selected.thumbnail" :alt="`${selected.title} 썸네일`" />
        </div>
        <div class="d-right">
          <div class="d-top">
            <img :src="selected.imageTop" :alt="`${selected.title} 이미지1`" />
          </div>
          <div class="d-bootom">
            <img :src="selected.imageBottom" :alt="`${selected.title} 이미지2`" />
          </div>
        </div>
      </div>
      <div class="desc">
        <span class="skill">
          <h3>SKILL</h3>
          <p class="tool">{{ selected.tool }}</p>
        </span>
        <p class="explanation">{{ selected.explanation }}</p>
        <!-- Figma 버튼: figmaUrl이 있을 때만 렌더링 -->
        <div v-if="selected.figmaUrl" class="figma-button">
          <a :href="selected.figmaUrl" target="_blank" rel="noopener noreferrer">
            🔗 Figma 디자인 보기
          </a>
        </div>

      </div>
    </div>
  </section>
  <section v-else>
    <p>해당 포트폴리오를 찾을 수 없습니다.</p>
  </section>
</template>

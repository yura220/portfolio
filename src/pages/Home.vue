<script setup>
import { onMounted, nextTick, onBeforeUnmount, watch } from 'vue'
import { useRoute } from 'vue-router'
import Title from '../components/Title.vue'
import Many from '../components/Many.vue'
import Stack from '../components/Stack.vue'
import Portfolio from '../components/Portfolio.vue'
import Happy from '../components/Happy.vue'
import Contact from '../components/Contact.vue'

const route = useRoute()
const emit = defineEmits(['scroll-change'])

// 💡 공통 스크롤 핸들러: '#many' 영역 기준으로 헤더 스타일 등 변경
function handleScroll() {
  const manyEl = document.querySelector('#many')
  if (!manyEl) return

  const top = manyEl.getBoundingClientRect().top
  const isPastMany = top <= 70 // 헤더 높이 기준
  emit('scroll-change', isPastMany)
}

onMounted(() => {
  handleScroll()
  window.addEventListener('scroll', handleScroll)

  // 쿼리로 들어온 경우 → DOM 로딩 약간 지연 후 스크롤 처리
  if (route.query.scrollTo) {
    setTimeout(() => {
      scrollToSection(route.query.scrollTo)
    }, 100)
  }
})


// ✅ 컴포넌트 unmount 시: scroll 이벤트 제거
onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll)
})

// 💡 특정 ID의 요소로 스무스하게 스크롤
function scrollToSection(id) {
  nextTick(() => {
    const el = document.getElementById(id)
    if (el) {
      el.scrollIntoView({ behavior: 'smooth' })
    }
  })
}

// ✅ query string이 변경될 경우에도 동적으로 스크롤 처리
watch(() => route.query.scrollTo, (newVal) => {
  if (newVal) scrollToSection(newVal)
})

defineProps(['footerClass'])
</script>

<template>
  <Title />
  <Many />
  <Stack />
  <Portfolio id="portfolio" />
  <Happy />
  <Contact id="contact" />
</template>

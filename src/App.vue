<!-- App.vue -->
<script setup>
import { ref, onMounted, onBeforeUnmount, computed, watch } from 'vue'
import { useRoute } from 'vue-router'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import './assets/reset.css'
import './app.css'
import './style.css'

const route = useRoute()
const enableScrollTrigger = ref(route.name === 'Home')
const isDark = ref(true)
const footerClass = ref('')
const updateFooterClass = (cls) => {
  footerClass.value = cls
}

// Home일 때만 scroll-trigger 기반 제어 허용
function handleScrollChange(val) {
  if (route.name === 'Home') {
    isDark.value = val
  }
}

watch(route, (newRoute) => {
  if (newRoute.name !== 'Home') {
    isDark.value = true
    enableScrollTrigger.value = false
  } else {
    enableScrollTrigger.value = true
  }

  if (newRoute.name !== 'About') {
    footerClass.value = ''
  }
})

const showSplash = ref(route.path === '/')

// 홈 진입 후 일정 시간 뒤에 splash 숨김
if (route.path === '/') {
  setTimeout(() => {
    showSplash.value = false
  }, 1500) // 1.5초 후 숨김
}

// 라우트 변경 시 splash 강제로 끔 (다른 페이지 재진입 방지)
watch(route, (newRoute) => {
  if (newRoute.path !== '/') {
    showSplash.value = false
  }
})

</script>

<template>
  <!-- ✅ Splash 화면 -->
  <!-- ✅ Splash 화면 -->
  <div v-if="showSplash" id="splash">
    <div class="zoom splash-fade" data-aos="zoom-in" data-aos-duration="1500">
      <svg width="300" height="300" viewBox="0 0 300 300">
        <defs>
          <clipPath id="logo-clip">
            <path d="M194.9,2.8c-0.8-1.4-2.3-2.2-4.3-2.2c-6.7,0.2-12,0.4-16.1,0.6c-4.1,0.2-9.2,0.3-15.5,0.3c-6.2,0-11.8-0.1-16.7-0.3
	C137.4,1,131.6,0.9,125,0.6c-1.9,0-3.2,0.7-4.1,2.2c-0.9,1.4-1.3,3-1.3,4.7c0.2,3.5,1,5.5,2.5,6c1.4,0.4,3.2,0.6,5.3,0.6
	c7.3,0,12.3,0.8,15,2.4c2.7,1.6,2.3,5.9-1.3,13l-34.7,68.5h-0.9C99.4,86.9,93.9,76,89,65.4S78.6,43.8,72.6,32.5
	C65.4,20,57.4,11.5,48.3,6.9C39.2,2.3,27.3,0,12.5,0C9.2,0,6.2,0.1,3.8,0.5C1.3,0.8,0,2.7,0,6.2c0,3.4,0.6,5.2,1.7,5.6
	c1.1,0.4,3.2,0.9,6.1,1.5c6.7,1.5,12.6,3.9,17.8,7.5c5.2,3.4,10,9.1,14.4,17c1.9,3.3,4.4,8.1,7.7,14.2c3.2,6.1,6.7,13,10.5,20.5
	c3.8,7.5,7.4,14.8,10.8,21.9c3.4,7.1,6.2,13.3,8.4,18.6c2.2,5.3,3.3,8.7,3.3,10.2v39.1c0,4-0.4,7.8-1.1,11.4
	c-0.7,3.7-2.5,6.7-5.1,9.1c-2.7,2.4-7.4,3.6-14.1,3.6c-2.1,0-3.9,0.2-5.3,0.6c-1.4,0.5-2.3,2.4-2.5,6c0,1.7,0.4,3.2,1.3,4.7
	c0.8,1.4,2.3,2.2,4.3,2.2c13.6-0.6,26.5-0.9,38.9-0.9c6.3,0,12.4,0.1,18.5,0.2c6,0.1,10,0.4,16.6,0.8c0.1,0,0.1,0,0.2,0
	c0.3,0,0.6,0,0.9-0.1c0.7,0,1.3,0,2.1,0c2.6,0,4.8-0.1,6.7-0.4c1.9-0.2,2.8-1.7,2.8-4.4c0-2.6-0.4-4-1.3-4.3
	c-0.9-0.3-2.5-0.7-4.7-1.2c-4.9-1-14.5-2.7-18.8-5.2c-0.1-0.1-0.2-0.1-0.3-0.2c-3.9-2.8-6.3-7.1-7-11.8c-0.5-3.2-0.8-6.5-1-9.9
	v-30.4c0-4.8,0.3-8.7,0.9-11.6c0.6-2.9,1.6-5.7,2.8-8.4c1.2-2.7,2.8-6,4.7-10l35.3-66.7c4-7.3,8.4-12.7,13.4-16.1
	c5-3.4,11.5-5.1,19.4-5.1c2.3,0,4.1-0.2,5.5-0.6c1.4-0.4,2.1-2.4,2.4-6C196.2,5.9,195.7,4.3,194.9,2.8z M175.3,81
	c-0.1-0.7-0.8-1-1.4-0.8c-1.4,0.6-3.9,1.7-5.8,2.3c-2.8,1-23.5,6-32.8,12.2c-10,6.7-18.1,18-17.3,30.5c0.9,13.1,4.7,16.2,4.7,16.2
	c9.2-27.9,27.3-37.5,35.2-40.6c0.5-0.2,0.8,0.5,0.4,0.8c-15.7,10.1-29.1,27.6-32.4,42.6c-2.1,9.6-2.9,18.4-3,20.8
	c0,0.4,0.2,0.8,0.5,1c1.5,1,2.8,0.9,3.7,0.5c0.8-0.3,1.2-1.1,1.1-2c-0.2-1.7-0.5-5,0-9.1c0.5-3.7,1.7-6.2,2.5-7.5
	c0.4-0.7,1.1-1,1.9-1c2.6,0,5-0.1,7.5-0.6c17.3-2.8,31-14.6,35.7-33.6c2.1-8.7,1.5-17.7,0.4-26.5C176,84.3,175.5,82.3,175.3,81z" />
          </clipPath>
        </defs>
        <image
          href="/img/bg2.gif"
          width="100%"
          height="100%"
          clip-path="url(#logo-clip)"
          preserveAspectRatio="xMidYMid slice"
        />
      </svg>
    </div>
  </div>
  <Header :is-dark="isDark" />
  <router-view v-slot="{ Component }">
    <component
      :is="Component"
      :footer-class="footerClass"
      @scroll-change="handleScrollChange"
    />
  </router-view>
  <Footer :extraClass="footerClass" />
</template>




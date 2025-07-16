<script setup>
import '../assets/portfolio.css'
import { onMounted } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
import portfolioData from '../js/portfolioData.js'
import { useRouter } from 'vue-router'

const router = useRouter()

gsap.registerPlugin(ScrollTrigger)

// ✅ 클릭 시 디테일 페이지로 이동
const goToDetail = (id) => {
  router.push(`/detail/${id}`)
}

onMounted(() => {
  gsap.timeline({
    scrollTrigger: {
      trigger: '#portfolio',
      start: 'top bottom',
      end: 'top 20%',
      scrub: true,
      markers: false,
    },
  })
  .fromTo(
    '.typo',
    { y: -350, opacity: 0 },
    { y: 0, opacity: 1, ease: 'power2.out' }
  )

  gsap.fromTo(
    '.gallery',
    { opacity: 0 },
    {
      opacity: 1,
      duration: 0.5,
      ease: 'power1.out',
      delay: 0.5,
      scrollTrigger: {
        trigger: '#portfolio',
        start: 'top 60%',
        toggleActions: 'play none none none',
        markers: false,
      }
    }
  )
})
</script>


<template>
  <section id="portfolio">
    <div class="wrap">
      <h2 class="typo">PORTFOLIO</h2>
      <ul class="gallery">
        <li v-for="item in portfolioData" :key="item.id">
            <a class="poimg" @click.prevent="goToDetail(item.id)">
            <img :src="item.thumbnail" :alt="item.title" />
            </a>
            <h3 class="h6">{{ item.title }}</h3>
            <span>
            <router-link :to="`/detail/${item.id}`" class="btn">DETAILS</router-link>
            <a :href="item.visitUrl" target="_blank" class="btn">VISIT</a>
            </span>
        </li>
        </ul>
    </div>
  </section>
</template>

<style scoped>
/* 필요하면 효과를 강조할 초기 상태 설정 */
.typo, .gallery {
  transition: opacity 0.3s ease-out;
}
</style>
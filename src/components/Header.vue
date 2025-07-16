<script setup>
import '../assets/header.css'
import { useRouter } from 'vue-router'

const router = useRouter()

function goToSection(sectionId) {
  router.push({ path: '/', query: { scrollTo: sectionId } })
}

defineProps({ isDark: Boolean })

function scrollToTop() {
  window.scrollTo({
    top: 0,
    behavior: 'smooth' // 부드럽게 이동
  })
}
</script>

<template>
  <header :class="{ dark: isDark }">
    <nav>
      <h1><router-link :class="{ 'ch_img': !isDark }" to="/" @click="scrollToTop">YURA</router-link></h1>
      <ul>
        <li>
          <router-link to="/about">ABOUT</router-link>
        </li>
        <li>
          <a href="#portfolio" @click.prevent="goToSection('portfolio')">PORTFOLIO</a>
        </li>
        <li>
          <a href="#contact" @click.prevent="goToSection('contact')">CONTACT</a>
        </li>
      </ul>
    </nav>
  </header>
</template>


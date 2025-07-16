<script setup>
import { useRoute } from 'vue-router'
import '../assets/footer.css'

const route = useRoute()
defineProps({
  extraClass: {
    type: String,
    default: ''
  }
})
</script>

<template>
  <footer id="footer":class="['footer', extraClass]">
    <p class="xs">
        @2025 YURA KYUNG.ALL RIGHTS RESERVED.<br>
        본 사이트는 상업적 목적이 아닌 개인 포트폴리오 사이트로 제작되었습니다.
    </p>
  </footer>
</template>
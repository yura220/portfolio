<script setup>
import '../assets/contact.css'
</script>

<template>
  <section id="contact">
    <div class="wrap flex-column-center">
        <h2 class="h1">Thank you for visiting!</h2>
        <div class="grid">
            <div class="thank_left">
                <p class="p">
                    포트폴리오를 방문해 주셔서 감사합니다.<br>
                    새로운 기회와 멋진 프로젝트에 대해 함께 이야기 나눌 수 있기를 기대합니다.<br>
                    저는 끊임없이 배우며 성장하는 웹퍼블리셔로서,<br>
                    사용자에게 가치 있는 경험을 제공하기 위해 노력하고 있습니다.
                </p>
                <p class="p">
                    문의나 협업 제안이 있다면 언제든 편하게 연락 주세요.<br>
                    소중한 메시지에 최대한 빠르고 성심껏 답변드리겠습니다!
                </p>
                <address>
                    <p class="num">Call<span>+82 10 9375 3759</span> </p>
                    <p class="mail">Email<span>ruddbfk7@gmail.com</span></p>
                </address>
            </div>
            <form>
                <input id="name" class="h6" type="text" placeholder="NAME">
                <input id="email" class="h6" type="email" placeholder="Email">
                <textarea id="message" placeholder="Your message"></textarea>
                <button type="submit" class="submit-button custom-btn btn-3"><span>SUBMIT</span></button>
            </form>
            <div class="social-links">
                <a href="#" target="_blank">GitHub</a>
                <a href="#" target="_blank">LinkedIn</a>
                <a href="#" target="_blank">Instagram</a>
                <a href="#" target="_blank">Resume</a>
            </div>
        </div>
    </div>
  </section>
</template>
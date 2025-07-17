<script setup>
import '../assets/contact.css'
import { ref } from 'vue'
import emailjs from 'emailjs-com'

const name = ref('')
const email = ref('')
const message = ref('')

const sendEmail = (e) => {
  e.preventDefault()

  emailjs.send('service_tk02r3q', 'template_zed0jjn', {
    name: name.value,
    email: email.value,
    message: message.value,
  }, 'Uvo8ZaAjfvJCz0D-G')
    .then(() => {
      alert("메일이 성공적으로 전송되었습니다.")
      name.value = ''
      email.value = ''
      message.value = ''
    })
    .catch((error) => {
      console.error("메일 전송 실패:", error)
      alert("메일 전송 중 오류가 발생했습니다.")
    })
}
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
            <form @submit="sendEmail">
                <input v-model="name" class="h6" type="text" placeholder="NAME" required>
                <input v-model="email" class="h6 email" type="email" placeholder="Email" required>
                <textarea v-model="message" placeholder="Your message" required></textarea>
                <button type="submit" class="submit-button custom-btn btn-3"><span>SUBMIT</span></button>
            </form>
            <div class="social-links">
                <a href="https://github.com/yura220" target="_blank">GitHub</a>
                <a href="#" target="_blank">LinkedIn</a>
                <a href="#" target="_blank">Instagram</a>
                <a href="#" target="_blank">Resume</a>
            </div>
        </div>
    </div>
  </section>
</template>
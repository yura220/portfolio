<!-- src/components/Title.vue -->
<script setup>
import '../assets/title.css'
</script>

<template>
  <div id="title">
    <div class="wrap flex-column-center">
      <div>
        <h2 class="name">I'M YURA, AND I<br />
          <span class="content">
            <span class="content__container">
              <ul class="content__container__list">
                <li class="content__container__list__item">WEB CREATOR!</li>
                <li class="content__container__list__item">CREATIVE DEVELOPER!</li>
                <li class="content__container__list__item">FRONT-END DESIGNER!</li>
                <li class="content__container__list__item">DESIGN TECHNOLOGIST!</li>
                <li class="content__container__list__item">WEB CREATOR!</li>
              </ul>
            </span>
          </span>
        </h2>
      </div>
    </div>
    <video autoplay loop muted>
      <source src="https://cdn.pixabay.com/video/2023/03/01/152740-803732906_large.mp4" type="video/mp4" />
    </video>
  </div>
</template>


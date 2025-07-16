<script setup>
import '../assets/many.css'
import { onMounted, nextTick } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

function initScrollTrigger() {
  const scrollEl = document.querySelector('.inner-scroll')
  const scrollLength = 2600 // 수동 지정 or scrollEl.scrollHeight 도 가능

  ScrollTrigger.create({
    trigger: '#many',
    start: 'top top',
    end: `+=${scrollLength}`,
    pin: true,
    pinSpacing: true,
    scrub: true,
  })

  gsap.fromTo(
    '.inner-scroll',
    { y: 0 },
    {
      y: -scrollLength,
      scrollTrigger: {
        trigger: '#many',
        start: 'top top',
        end: `+=${scrollLength}`,
        scrub: true,
      },
    }
  )

  ScrollTrigger.refresh()
}

onMounted(() => {
  nextTick(() => {
    requestAnimationFrame(() => {
      requestAnimationFrame(() => {
        initScrollTrigger() // ✅ 누락되어 있던 부분
      })
    })
  })
})

</script>

<template>
  <section id="many">
    <div class="many-bg">
        <img src="/img/many.jpg">
    </div>
    <div class="flex-column-center">
      <!-- 좌측 Article -->
      <article>
        <h2>I’M MANY<br />THINGS.</h2>
        <p class="p">
          <span>#Graphics #Web #Writing #Efficient #Responsible<br />
            저는 한 가지 모습에 머물지 않습니다. 창작하고, 개발하며, 늘 새로운 것에<br />
            도전합니다. 저의 여러 가지 모습을 이곳에서 확인할 수 있습니다.</span>
        </p>
      </article>

      <!-- 우측 box -->
      <div class="right-section">
        <div class="box pinned-section">
          <ul class="inner-scroll">
            <li>
              <div class="inner-box">
                <h3>다양한 소재, 무한한 표현</h3>
                <p class="p">6년간 판촉물, 프랜차이즈, 카드 업계 등 다양한 분야에서<br />
                  편집디자이너로 일하며 폭넓은 경험을 쌓아왔습니다.<br />
                  다양한 소재와 형식의 인쇄물을 다루며 실무 감각을 키웠고,<br />
                  그래픽 디자인에 대한 깊이 있는 이해를 바탕으로 효과적인<br />
                  비주얼 커뮤니케이션을 만들어갑니다.</p>
              </div>
            </li>
            <li>
              <div class="inner-box">
                <h3>믿음을 주는 마무리</h3>
                <p class="p">맡은 일은 끝까지 책임지고 완성하는 것이<br />
                  가장 중요하다고 생각합니다.<br />주어진 마감 기한을 철저히 지키면서도 퀄리티를<br />
                  유지하기 위해 계획적으로 작업을 진행합니다.<br />
                  시작한 일은 끝까지 마무리하는 성향 덕분에<br />
                  신뢰를 받으며, 책임감 있는 태도로 업무를<br />
                  수행하는 것을 원칙으로 삼고 있습니다.</p>
              </div>
            </li>
            <li>
              <div class="inner-box">
                <h3>웹사이트, 더 나은 경험을 고민하다</h3>
                <p class="p">편집디자이너로 일하면서 사내 홈페이지 관리를 위해<br />코딩을 배우기 시작했고, 카페24와 고도몰을 활용해<br />홈페이지 유지·보수를
                  담당했습니다.<br />이후 퍼블리싱과 프론트엔드 과정을 수료하며 더욱<br />깊이 있는 기술을 익혔고, 이제는 직접 홈페이지<br />제작까지 가능합니다.</p>
              </div>
            </li>
            <li>
              <div class="inner-box">
                <h3>읽고 싶어지는 글을 쓰다</h3>
                <p class="p">취업 전, 1년간 계약직으로 온라인 마케팅을<br />경험한 것을 계기로 자연스럽게 개인 블로그를<br />운영하기 시작했습니다.<br />단순한
                  기록을 넘어, 정보를 효과적으로 전달하는 글을<br />쓰기 위해 고민하고 연구하며 글쓰기 능력을<br />발전시켜 왔습니다.</p>
              </div>
            </li>
            <li>
              <div class="inner-box">
                <h3>속도와 완성도의 균형</h3>
                <p class="p">더 효율적인 방법을 고민하는 것은<br />제 업무 방식의 핵심입니다.<br />작업을 할 때마다 어떻게 하면 더 빠르고<br />효과적으로
                  처리할 수 있을지 연구하고,<br />실제로 적용하며 업무 속도를 높여왔습니다.<br />덕분에 ‘손이 빠르다’는 말을 자주 들어왔으며,<br />빠르면서도
                  정확한 결과물을 만들어내는 것에 자신이 있습니다.</p>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

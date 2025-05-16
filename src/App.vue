<template>
  <h1>Zootopia 굿즈샵</h1>
  <div v-for="(item, index) in products" :key="index">
    <h4>{{ item }} 굿즈</h4>
    <p>{{ prices[index] }} 만원</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  // Data 보관함
  data() {
    return {
      price1: 5,
      price2: 3,

      products: ['판다', '호랑이'],
      prices: [5, 3],
      // 용도
      // 1) hard-coding 시 변경이 어려움 (데이터 저장후 binding)
      // 2) Vue 실시간 자동 렌더링 기능 사용 (html에 실시간 반영 적용) -> WEBAPP 개발 가능!
      // html 속성도 binding 가능 (:속성="데이터이름")
    }
  },
  components: {},
}
</script>

<style></style>

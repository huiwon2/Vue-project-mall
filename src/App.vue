<template>
  <h1>Zootopia 굿즈샵</h1>
  <!-- Navigation Bar -->
  <div class="menu">
    <!-- key: 반복문 돌면서 변하는 숫자/문자 -->
    <!-- v-for 변수 2개까지 선언 가능 -->
    <a v-for="(name, index) in menu" :key="index">{{ name }}</a>
  </div>

  <div v-for="(item, index) in products" :key="index">
    <h4>{{ item }} 굿즈</h4>
    <p>{{ prices[index] }} 만원</p>
    <button class="alertButton" @click="alertCount[index]++">🚨</button>
    <span> {{ alertCount[index] }} </span>
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
      menu: ['Home', 'Products', 'About'],
      alertCount: [0, 0, 0],
      // 용도
      // 1) hard-coding 시 변경이 어려움 (데이터 저장후 binding)
      // 2) Vue 실시간 자동 렌더링 기능 사용 (html에 실시간 반영 적용) -> WEBAPP 개발 가능!
      // html 속성도 binding 가능 (:속성="데이터이름")
    }
  },
  methods: {
    // Vue 함수 정의 코드
    // data에 있는 데이터를 사용하려면 this.데이터명으로 사용해야 가능
  },
  components: {},
}
</script>

<style>
#app {
  font-family: Avenir, Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu {
  background: lightblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.alertButton {
  border: none;
  background: none;
  cursor: pointer;
}
</style>

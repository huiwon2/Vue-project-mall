<template>
  <!-- 모달창 -->
  <!-- v-if : Vue 조건식 -->
  <div class="black-bg" v-if="isOpened == true">
    <div class="white-bg">
      <button class="close-btn" @click="isOpened = false">X</button>
      <h4>{{ selectedProduct }} 인형</h4>
      <p>설명</p>
    </div>
  </div>

  <h1>Zootopia 굿즈샵</h1>
  <!-- Navigation Bar -->
  <div class="menu">
    <!-- key: 반복문 돌면서 변하는 숫자/문자 -->
    <!-- v-for 변수 2개까지 선언 가능 -->
    <a v-for="(name, index) in menu" :key="index">{{ name }}</a>
  </div>

  <div v-for="(item, index) in products" :key="index">
    <img :src="imgLink[index]" class="item-img" />
    <h4 @click="openModal(item)">{{ item }} 굿즈</h4>
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
      isOpened: false,
      selectedProduct: undefined,
      price1: 5,
      price2: 3,

      products: ['판다', '호랑이'],
      prices: [5, 3],
      menu: ['Home', 'Products', 'About'],
      alertCount: [0, 0, 0],
      imgLink: ['./src/assets/products/baofamily.png', './src/assets/products/tiger.png'],
      // 용도
      // 1) hard-coding 시 변경이 어려움 (데이터 저장후 binding)
      // 2) Vue 실시간 자동 렌더링 기능 사용 (html에 실시간 반영 적용) -> WEBAPP 개발 가능!
      // html 속성도 binding 가능 (:속성="데이터이름")
    }
  },
  methods: {
    // Vue 함수 정의 코드
    // data에 있는 데이터를 사용하려면 this.데이터명으로 사용해야 가능
    openModal(product) {
      this.selectedProduct = product
      this.isOpened = true
    },
  },
  components: {},
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
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
.item-img {
  margin-top: 50px;
  width: 10%;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rbga(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
  display: flex;
  justify-content: center; /* 수평 중앙 */
  align-items: center; /* 수직 중앙 */
}
.white-bg {
  position: relative;
  width: 80%;
  height: 50%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.close-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  border: none;
  background: none;
  font-size: 18px;
  cursor: pointer;
}
</style>

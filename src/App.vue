<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div>
    <!-- html 속성도 데이터바인딩 가능 -> :속성="데이터테이블" -->
    <h4 :style="styleH">{{ products[0] }}</h4>
    <p>{{ price1 }} 만원</p>
  </div>

  <div>
    <h4>{{ products[1] }}</h4>
    <p>{{ price2 }} 만원</p>
  </div>

  <div>
    <h4>{{ products[2] }}</h4>
    <p>{{ price2 }} 만원</p>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      price1 : 60,
      price2 : 70,
      styleH : 'color : blue',
      products : ['역삼동 오피스텔', '천호동 오피스텔', '마포구 오피스텔'],
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <div class="menu">
    <a>Home</a>
    <a>Shop</a>
    <a>About</a>
  </div>

  <div v-for="(a, i) in products" :key="i">
    <!-- html 속성도 데이터바인딩 가능 -> :속성="데이터테이블" -->
    <h4 :style="styleH">{{ products[i] }}</h4>
    <p>{{ price[i] }} 만원</p>
    <button @click="increase(i)">허위매물 신고</button> <span>신고수 : {{ count[i] }}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      price : [60, 70, 100],
      styleH : 'color : blue',
      products : ['역삼동 오피스텔', '천호동 오피스텔', '마포구 오피스텔'],
      count : [0, 0, 0],
    }
  },

  methods : {
    increase(props) {
      this.count[props] ++;
    },
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
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  text-decoration: none;
  padding: 10px;
}
</style>

<template>
  <div class="black-bg" v-if="modal">
    <div class="white-bg">
      <h4>{{ products[clickNum].title }}</h4>
      <p>{{ products[clickNum].price }}</p>
      <button @click="modal = false">close</button>

      <div v-if="clickNum === 1">
        clickNum1
      </div>
      <div v-else-if="clickNum === 2">
        clickNum2
      </div>
      <div v-else>
        clickNum
      </div>
    </div>
  </div>

  <div class="menu">
    <a>Home</a>
    <a>Shop</a>
    <a>About</a>
  </div>

  <div v-for="(a, i) in products" :key="i">
    <img :src="products[i].image" :style="room-img"/>
    <!-- html 속성도 데이터바인딩 가능 -> :속성="데이터테이블" -->
    <h4 :style="styleH" @click="modal = true; clickNum = i">{{ products[i].title }}</h4>
    <p>{{ products[i].price }} 만원</p>
    <!-- <button @click="increase(i)">허위매물 신고</button> <span>신고수 : {{ count[i] }}</span> -->
  </div>
</template>

<script>

import data from './data.js';

export default {
  name: 'App',
  data() {
    return {
      price : [60, 70, 100],
      styleH : 'color : blue',
      // products : ['역삼동 오피스텔', '천호동 오피스텔', '마포구 오피스텔'],
      products : data,
      count : [0, 0, 0],
      modal : false,
      clickNum : 0,
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
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

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

.room-img {
  width: 100%;
  margin-top: 40px;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0, 5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; 
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>

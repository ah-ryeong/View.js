<template>

  <Modal :products="products" :modal="modal" :clickNum="clickNum" />

  <div class="menu">
    <a>Home</a>
    <a>Shop</a>
    <a>About</a>
  </div>

  <Discount />

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
import Discount from './Discount.vue';
import Modal from './Modal.vue';

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
    Discount,
    Modal,
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

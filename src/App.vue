<template>

  <Modal :products="products" :modal="modal" :clickNum="clickNum" />

  <div class="menu">
    <a>Home</a>
    <a>Shop</a>
    <a>About</a>
  </div>

  <Discount v-bind="obj" :name="obj.name" />

  <Card :products="products[i]" v-for="(product, i) in products" :key="product"/>
</template>

<script>

import data from './data.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

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
      obj : { name : 'kim', age: 20 },
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
    Card,
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

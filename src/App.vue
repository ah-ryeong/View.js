<template>

  <!-- <div class="start" :class="{ end : modal }"> -->
  <Transition name="fade">
    <Modal @closeModal="modal = false" :products="products" :modal="modal" :clickNum="clickNum" />
  </Transition>

  <div class="menu">
    <a>Home</a>
    <a>Shop</a>
    <a>About</a>
  </div>

  <Discount v-if="showDiscount === true" v-bind="obj" :name="obj.name" />

  <button class="priceBtn" @click="priceSort">가격순 정렬</button>
  <button class="priceBtn" @click="priceSort2">가격높은순정렬</button>
  <button class="priceBtn" @click="abc">가나다순정렬</button>

  <Card @openModal="modal = true; clickNum = $event" :products="products[i]" v-for="(product, i) in products" :key="product"/>
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
      showDiscount : true,
    }
  },

  methods : {
    increase(props) {
      this.count[props] ++;
    },

    priceSort() {
      this.products.sort(function(a, b) {
        return a.price - b.price;
      });
    },

    priceSort2() {
      this.products.sort((a, b) => {
        return b.price - a.price;
      });
    },

    abc() {
      this.products.sort((a, b) => {
        if(a.title > b.title) {
          return 1;
        } else {
          return -1;
        }
      });
    }
  },

  mounted(){
    setTimeout(() => {
      this.showDiscount = false;
    }, 2000);
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

.start {
  opacity: 0;
  transition: all 1s;
}

.end {
  opacity: 1;
}

/* 시작 */
.fade-enter-from {
  opacity: 0;
} 

.fade-enter-active {
  transition: all 1s;
}

/* 끝 */
.fade-enter-to {
  opacity: 1;
}

/* 퇴장은 .fade-leave-from / active / to */

.priceBtn {
  margin-bottom: 20px;
  margin-right: 5px;
  margin-top: 20px;
}
</style>

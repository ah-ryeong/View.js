<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div >
        <img :src="products.image" :style="room-img"/>
        <!-- html 속성도 데이터바인딩 가능 -> :속성="데이터테이블" -->
        <h4 @click="$emit('openModal', products.id)">{{ products.title }}</h4>
        <p>{{ products.price }} 만원</p>
        <!-- <button @click="increase(i)">허위매물 신고</button> <span>신고수 : {{ count[i] }}</span> -->
    </div>
</template>

<script>
    export default {
        // eslint-disable-next-line vue/multi-word-component-names
        name : 'Card',
        props : {
            products : Object,
        }
    }
</script>

<style></style>

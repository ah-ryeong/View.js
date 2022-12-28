<template> 
    <div class="black-bg" v-if="modal">
        <div class="white-bg">
        <h4>{{ products[clickNum].title }}</h4>
        <h4>{{ products[clickNum].content }}</h4>
        <!-- <input @input="month = $event.target.value"> -->
        <input v-model.number="month">
        <p>{{ month }}개월 선택함 : {{ (products[clickNum].price) * month }}원</p>
        <button @click="$emit('closeModal')">close</button>

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
</template>

<script>
    export default {
        // eslint-disable-next-line vue/multi-word-component-names
        name: 'Modal',
        data() {
            return {
                month : 1,
            }
        },

        watch : {
            month(value) {
                if(value >= 13) {
                    alert('13 이상 입력할 수  없습니다.');
                    this.month = 1;
                } else if(isNaN(value) === true) {
                    alert('문자는 입력할 수 없습니다.');
                    this.month = 1;
                }
            }
        },

        props : {
            products : Array,
            modal : Boolean,
            clickNum : Number,
        }
    }
</script>

<style>

</style>
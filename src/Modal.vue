<template> 
    <div class="black-bg" v-if="modal">
        <div class="white-bg">
        <h4>{{ products[clickNum].title }}</h4>
        <h4>{{ products[clickNum].content }}</h4>
        <p>{{ products[clickNum].price }}</p>
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
        props : {
            products : Array,
            modal : Boolean,
            clickNum : Number,
        }
    }
</script>

<style>

</style>
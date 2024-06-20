<template>

    <div class="header" @click="onClick">
        <div class="header-title">{{ title }}</div>
        <img :src="arrow" class="arrow" :class="{closed: show}" alt="">
    </div>

    <AccordionContentLoading v-if="loading" />
    <div v-if="show" class="content">{{ content }}</div>


 </template>

<script>


import AccordionContentLoading from "@/components/AccordionContentLoading.vue"
import arrowImg from "@/assets/arrow.svg"

export default {

    name: 'AccordionComponent',
    props: {
        accordionData: Array,
        show: Boolean,
        content: String,
        title: String,
        loading: Boolean
    },
    emits: ['clicked'],
    data () {
        return {
            arrow: arrowImg,
        }
    },
    methods: {
        onClick () {
            this.$emit('clicked')
        }
    },
    components: {
        AccordionContentLoading
    }
}

</script>


<style scoped>

.header, .content {
    padding: .7rem;
}

.header {
    display: flex;
    justify-content: space-between;
    cursor: pointer;
    background: #ededed;
    font-weight: bold;
}

.arrow {
    height: 1rem;
}

.closed {
    transform: rotateX(180deg);
    transition: all .3s linear
}

</style>
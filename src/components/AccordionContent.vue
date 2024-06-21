<template>

    <div class="header" @click="onClick">
        <div class="header-title">{{ title }}</div>
        <img :src="arrow" class="arrow" :class="{closed: show || loading}" alt="">
    </div>
    <TransitionGroup name="open-loading">
        <AccordionContentLoading v-if="loading" class="content"/>
    </TransitionGroup>
    <TransitionGroup name="open-content">
        <div v-if="show" class="content">{{ content }}</div>
    </TransitionGroup>


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

.header {
    padding: .7rem;
}

.header, .content {
    box-sizing: border-box;
    border: 1px solid #ededed;
    overflow: hidden;
}

.content {
    transition: all 1s ease-out
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
    transition: all .3s linear
}

.closed {
    transform: rotateX(180deg);
    transition: all .3s linear
}

.open-content-enter-from,
.open-content-leave-to {
    max-height: 0rem;
}

.open-content-leave-from,
.open-content-enter-to {
    max-height: 100%;
}

.open-content-enter-active,
.open-content-leave-active {
    transition: all 1s ease-out;
}

.open-loading-enter-from,
.open-loading-leave-to {
    max-height: 0rem;
}

.open-loading-leave-from,
.open-loading-enter-to {
    max-height: 100%;
}


.open-loading-enter-active{
    transition: all 1s ease-out;
}
.open-loading-leave-active {
    transition: all 0s ease-out;
}

</style>
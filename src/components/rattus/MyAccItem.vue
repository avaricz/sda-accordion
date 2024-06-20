<template>
    <div class="header" @click="$emit('click', index)">
        <div class="header-title">{{ item.title }}</div>
        <img :src="arrow" class="arrow" :class="{ closed: isOpen }" alt="arrow">
    </div>

    <transition name="efect">
        <div v-if="isOpen" class="content">{{ item.content }}</div>
    </transition>
</template>

<script>

import arrowImg from "@/assets/arrow.svg"

export default {
    name: 'MyAccItem',
    props: {
        item: Object,
        index: Number,
        openedIndex: Number,
    },
    computed: {
        arrow() {
            return arrowImg;
        },
        isOpen() {
            return this.openedIndex === this.index;
        }
    },
}

</script>

<style scoped>

.header,
.content {
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

.efect-enter-from,
.efect-leave-to {
    max-height: 0;
}

.efect-enter-to,
.efect-leave-from {
    max-height: 100%;
}

.efect-enter-active {
    transition: all .5s linear
}

.efect-leave-active {
    animation: all .5s linear
}
</style>
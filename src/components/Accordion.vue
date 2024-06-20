<template>

    <div class="container">

        <AccordionContent 
        v-for="(item, index) in accordionData" 
        :key="index"
        :title="item.title"
        :content="item.content"
        :show="show[index]"
        @clicked="onClicked(index)"
        :loading="loadContent" <!-- TODO -->
        />

    </div>

</template>

<script>

import AccordionContent from '@/components/AccordionContent.vue'
import { getData } from '@/challenge.js'


export default {
    name: 'Accordion',
    data() {
        return {
            accordionData: [
                {title: "První Item", content: "loading..."},
                {title: "Druhý Item", content: "Loading..."},
                {title: "Třetí Item", content: "loading..."}
            ],
            show: [],
            loadContent: false
        }
    },
    created () {
        this.accordionData.forEach(() => {
            this.show.push(false)
        })
    },
    methods: {
        onClicked (index) {
            this.show[index] = !this.show[index]
            this.loadData(index)
            
        },
        async loadData(index) {
            
            const data = await getData(index)
            this.accordionData[index].content = data
            
            
        }
    },
    components: {
        AccordionContent,
    }
}

</script>

<style scoped>

.container {
    display: flex;
    flex-direction: column;
    border: 1px solid #cdcdcd;
    border-radius: 5px;
    overflow: hidden;
    width: 100%;
    max-width: 400px;
}

</style>
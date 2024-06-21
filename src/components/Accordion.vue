<template>

    <div class="container">

        <AccordionContent 
        v-for="(item, index) in accordionData" 
        :key="index"
        :title="item.title"
        :content="item.content"
        :show="show[index]"
        @clicked="onClicked(index)"
        :loading="showLoading[index]" 
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
                {title: "První Item", content: ""},
                {title: "Druhý Item", content: ""},
                {title: "Třetí Item", content: ""}
            ],
            show: [],
            showLoading:[] ,
            filledContent: []
        }
    },
    created () {
        this.accordionData.forEach(() => {
            this.show.push(false)
            this.showLoading.push(false)
        })
    },
    methods: {
        onClicked (index) {
            if (this.accordionData[index].content === "") {
                this.loadData(index)

                this.showLoading[index] = !this.showLoading[index]
                return
            }
            this.show[index] = !this.show[index]
            
            
            
        },
        async loadData(index) {
            const data = await getData(index)
            this.accordionData[index].content = data
            this.filledContent[index] = true
            this.showLoading[index] = !this.showLoading[index]
            this.show[index] = !this.show[index]
        },
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
    border-radius: 5px;
    overflow: hidden;
    width: 100%;
    max-width: 400px;
}

</style>
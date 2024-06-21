<template>

    <div>... Loading ...</div>

</template>

<script>

export default {
    name:'AccordionContentLoading',

    
}

</script>


<style scoped>


@keyframes example {
  0% {color: lightgray;}
  50% {color: gray;}
  100% {color: lightgray;}

}

div {
    text-align: center;
    animation-name: example;
    animation-duration: 1s;
    animation-iteration-count:infinite;
}
</style>
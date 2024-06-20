<template>

<h1>Home</h1>

  <Accordion />


</template>

<script>

import Accordion from "@/components/Accordion.vue"

export default {

  name: 'App',
  components: { Accordion }
}

</script>

<style>

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content:flex-start;
  height: 100vh;
  font-family: system-ui;
}

</style>
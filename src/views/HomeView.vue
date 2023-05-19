<script setup>
import { Transition } from 'vue';
import { ref } from 'vue'

const Greeting = ref(true)
</script>

<template>
  <div class="container">
    <Transition name="fade">
      <h1 v-if="Greeting">Hello World</h1>
      <h1 v-else>Good Buy</h1>
    </Transition>
    <button @click="Greeting = !Greeting">Show</button>
  </div>
</template>

<style scoped>
.fade-enter-from {
  opacity: 0;
}

.fade-enter-to {
  opacity: 1;
}

.fade-enter-active {
  transition: all .5s ease;
}


.fade-leave-from {
  opacity:1;
}

.fade-leave-to {
  opacity: 0;
}

.fade-leave-active {
  transition: all .5s ease;
}

.container{
  position: relative;
}

h1{
  position: absolute;
}

button{
  margin-top: 50px;
}
</style>
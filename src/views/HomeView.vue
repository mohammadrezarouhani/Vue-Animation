<script setup>
import { Transition } from 'vue';
import { ref } from 'vue'

const nameList = ref(["mohammadreza", "amir"])
const invitee = ref("")

const addInvitee = () => {
  nameList.value.unshift(invitee.value)
  invitee.value = ""
}

const removeName=(name)=>{
  nameList.value=nameList.value.filter(n=>n!=name)
}
</script>

<template>
  <div class="container">
    <input v-model="invitee" type="text" placeholder="Enter Invitee Name" @keypress.enter="addInvitee">
    <ul>
      <TransitionGroup name="Invitee">
        <li v-for="name in nameList" :key="name" @click="removeName(name)">{{ name }}</li>
      </TransitionGroup>
    </ul>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.container input {
  width: 500px;
  height: 50px;
  border-radius: 5px;
  border: 1px solid rgba(128, 128, 128, .13);
  box-shadow: 1px 1px 10px rgba(0, 0, 0, .12);
  margin-top: 20px;
  padding: 10px;
}

.container ul {
  padding: 0px;
  margin: 20px;
}

.container ul li {
  list-style: none;
  width: 300px;
  height: 50px;
  border-radius: 5px;
  border: 1px solid rgba(128, 128, 128, .13);
  text-align: center;
  padding: 15px;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, .12);
  margin-top: 10px;
}

.container ul li:hover {
  border: 1px solid blueviolet;
}


/* Transition */
.Invitee-enter-from {
  opacity: 0;
  transform: scale(0);
}

.Invitee-enter-to {
  opacity: 1;
  transform: scale(1);
}

.Invitee-enter-active {
  transition: all .5s ease;
}

.Invitee-leave-from {
  opacity: 1;
  transform: scale(1);
}

.Invitee-leave-to {
  opacity: 0;
  transform: scale(0);
}

.Invitee-leave-active {
  transition: all .5s ease;
  position: absolute;
}

.Invitee-move{
  transition: all .5s ease;
}
</style>
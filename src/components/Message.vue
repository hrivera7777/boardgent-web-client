<script setup>
import { ref } from "vue";
import { useSocketIO } from "../helpers/socket.io";

defineProps({
  msg: String,
});

const { socket } = useSocketIO();
socket.on("Socket-messages", () => {
  console.log("Hi hi :)");
});

const count = ref(0);
</script>

<template>
  <div
    class="p-5 shadow-xl shadow-indigo-500/50 rounded-xl mx-auto my-auto w-fit h-96 grid grid-flow-row bg-gradient-to-r from-cyan-500 to-blue-500"
  >
    <h2 class="text-white m-auto text-2xl display: inline;">
      This is a web app that uses websocket
    </h2>
    <div class="flex flex-row">
      <p class="text-lg mr-5 my-auto text-white">Serial number: 112343</p>
      <img class="h-64 w-60" src="../assets/images/pc.png" alt="pcImage" />
    </div>
    <!-- <button class="rounded-lg bg-orange-400" type="button" @click="count++">
      count is: {{ count }}
    </button> -->
  </div>
</template>

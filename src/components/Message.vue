<script setup>
import { ref, onMounted } from "vue";
import { useSocketIO } from "../helpers/socket";

let messageReceived = ref("waiting");
onMounted(() => {
  const { socket } = useSocketIO();
  socket.on("msgToClient", (message) => {
    saveMessage(message);
  });
});

const saveMessage = (message) => {
  messageReceived.value = message;
};
</script>

<template>
  <div
    class="p-5 shadow-xl shadow-indigo-500/50 rounded-xl mx-auto my-auto w-fit h-96 grid grid-flow-row bg-gradient-to-r from-cyan-500 to-blue-500"
  >
    <h2 class="text-white m-auto text-2xl display: inline;">
      This is a web app that uses websocket
    </h2>
    <div class="flex flex-row">
      <p class="text-lg mr-5 my-auto text-white">
        Serial number: {{ messageReceived }}
      </p>
      <img class="h-64 w-60" src="../assets/images/pc.png" alt="pcImage" />
    </div>
  </div>
</template>

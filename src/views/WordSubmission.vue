<template>
<h1>Co-op mode</h1>

<newPageButton v-bind:text="uiLabels.enterWordHere" to="/hostLobby/"></newPageButton>

</template>

<script>
import io from 'socket.io-client';
import newPageButton from '../components/Button.vue';
const socket = io("localhost:3000");

export default {
  name: 'CreateView',
  components: {
    newPageButton
  },
  data: function () {
    return {
     
      uiLabels: {},
    }
  },
  created: function () {
    socket.on( "uiLabels", labels => this.uiLabels = labels );
    socket.emit( "getUILabels", this.lang );
  }
}



</script>

<style scoped>

</style>
<template>
    <h1>The lobby for the host</h1>
    <h3>Waiting in vain...</h3>
    <newPageButton v-bind:text="uiLabels.start" to="/toInGameHostView/" />
    
    <p>Current word:</p>
    
    </template>
    
    <script>
    import io from 'socket.io-client';
    import newPageButton from '../components/Button.vue';
    const socket = io("localhost:3000");
    
    export default {
      name: 'lobbyForHost',
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